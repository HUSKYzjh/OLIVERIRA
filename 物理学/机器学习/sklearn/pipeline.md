## 知识
在讲管道之前我们先了解一下 scikit-learn 中的两个概念**Transformer**和**Estimator**

- **Transformer**：转换器是指具有 fit() 和 transform() 方法的对象，用于清理、减少、扩展或生成特征。简而言之，转换器可帮助您将数据转换为机器学习模型所需的格式。 OneHotEncoder 和 MinMaxScaler 是转换器的示例。Transformer主要用于在特征工程上。如特征编码，归一化等等。
- **Estimator**：估计器是指机器学习模型。它是一个带有 fit() 和 predict() 方法的对象。我们将在本文中交替使用估算器和模型。如 RandomFroest(),SVM()。

### 好处
1. **微调管道的能力**：在构建模型时，您是否曾经不得不回过头来尝试不同的方法来预处理数据并再次运行模型，以查看预处理步骤中的调整是否提高了模型的适应度？在优化模型时，参数不仅存在于模型超参数中，还存在于预处理步骤的实现中。考虑到这一点，当我们有一个统一转换器和估计器的单个管道对象时，我们能够微调整个管道的超参数，包括转换器和具有 GridSearchCV 或 RandomizedSearchCV 的估计器
2. **更容易部署**：在训练模型时用于准备数据的所有转换步骤也应在进行预测时应用于生产环境中的数据。当我们训练流水线时，我们训练包含数据转换器和模型的单个对象。经过训练后，此 Pipeline 对象可用于更顺畅的部署

## sklearn
`sklearn.pipeline.Pipeline(steps, memory=None, verbose=False)

### Parameters

- **steps** : 步骤：列表(list)  
    被连接的（名称，变换）元组（实现拟合/变换）的列表，按照它们被连接的顺序，最后一个对象是估计器(estimator)。
- **memory**:内存参数,Instance of sklearn.external.joblib.Memory or string, optional (default=None)
- **name_steps**: bunch object，属性,具有属性访问权限的字典  
    只读属性以用户给定的名称访问任何步骤参数。键是步骤名称，值是步骤参数。或者也可以直接通过”.步骤名称”获取

### funcution

- Pipline的方法都是执行各个学习器中对应的方法,如果该学习器没有该方法,会报错
- 假设该Pipline共有n个学习器
- transform,依次执行各个学习器的transform方法
- fit,依次对前n-1个学习器执行fit和transform方法,第n个学习器(最后一个学习器)执行fit方法
- predict,执行第n个学习器的predict方法
- score,执行第n个学习器的score方法
- set_params,设置第n个学习器的参数
- get_param,获取第n个学习器的参数

使用 pipeline 后，我们每一步的输出都会自动的作为下一个的输入。此时我们可以在 pipeline 中加入模型进行从特征到模型的训练

估计器只能放在pipeline的最后一个。名字用于使用pipeline进行字典访问。