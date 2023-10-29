 支持向量分类器
 `sklearn.svm.SVC(C=1.0, kernel=’rbf’, degree=3, gamma=’auto_deprecated’, coef 0=0.0, shrinking=True, probability=False, tol=0.001, cache_size=200, class_weight=None, verbose=False, max_iter=-1, decision_function_shape=’ovr’, random_state=None)
 
 ### 参数
 参数：

**C** ： float，可选 (默认值= 1.0)
错误术语的惩罚参数 C。C 越大，相当于惩罚松弛变量，希望松弛变量接近 0，即对误分类的惩罚增大，趋向于对训练集全分对的情况，这样对训练集测试时准确率很高，但泛化能力弱。C 值小，对误分类的惩罚减小，允许容错，将他们当成噪声点，泛化能力较强。

**kernel** ： string，optional (default =‘rbf’)
[[核函数]]类型，str 类型，默认为’rbf’。可选参数为：

’**linear**’：线性核函数
‘**poly**’：多项式核函数
‘**rbf**’：径像核函数/[[高斯]]核
‘**sigmod**’：sigmod 核函数
‘**precomputed**’：核矩阵
precomputed 表示自己提前计算好核函数矩阵，这时候算法内部就不再用核函数去计算核矩阵，而是直接用你给的核矩阵，核矩阵需要为 $n*n$ 的。

**degree** ： int，可选 (默认= 3)
多项式核函数的阶数，int 类型，可选参数，默认为 3。这个参数只对多项式核函数有用，是指多项式核函数的阶数 n，如果给的核函数参数是其他核函数，则会自动忽略该参数。

**gamma** ： float，optional (默认=‘auto’)
核函数系数，float 类型，可选参数，默认为 auto。只对’rbf’ ,’poly’ ,’sigmod’有效。如果 gamma 为 auto，代表其值为样本特征数的倒数，即 1/n_features。

**coef** 0 ： float，optional (默认值= 0.0)
核函数中的独立项，float 类型，可选参数，默认为 0.0。只有对’poly’和,’sigmod’核函数有用，是指其中的参数 c。

**shrinking** ： 布尔值，可选 (默认= True)
是否采用启发式收缩方式，bool 类型，可选参数，默认为 True。

**probability** ： 布尔值，可选 (默认=False)
是否启用概率估计，bool 类型，可选参数，默认为 False，这必须在调用 fit ()之前启用，并且会 fit ()方法速度变慢。

**tol** ： float，optional (默认值= 1 e-3)
svm 停止训练的误差精度，float 类型，可选参数，默认为 1 e^-3。

**cache_size** ： float，可选（默认为 200）
内存大小，float 类型，可选参数，默认为 200。指定训练所需要的内存，以 MB 为单位，默认为 200MB。

**class_weight** ： {dict，‘balanced’}，可选
类别权重，dict 类型或 str 类型，可选参数，默认为 None。给每个类别分别设置不同的惩罚参数 C，如果没有给，则会给所有类别都给 C=1，即前面参数指出的参数 C。如果给定参数’balance’，则使用 y 的值自动调整与输入数据中的类频率成反比的权重。

**verbose** ： bool，默认值：False
是否启用详细输出，bool 类型，默认为 False，此设置利用 libsvm 中的每个进程运行时设置，如果启用，可能无法在多线程上下文中正常工作。一般情况都设为 False，不用管它。

**max_iter** ： int，optional (默认值= -1)
最大迭代次数，int 类型，默认为-1，表示不限制。

**decision_function_shape** ： ‘ovo’，‘ovr’，默认=‘ovr’
决策函数类型，可选参数’ovo’和’ovr’，默认为’ovr’。’ovo’表示 one vs one，’ovr’表示 one vs rest。

**random_state** ： int，RandomState 实例或 None，可选 (默认=无)
数据洗牌时的种子值，int 类型，可选参数，默认为 None。伪随机数发生器的种子, 在混洗数据时用于概率估计。
`