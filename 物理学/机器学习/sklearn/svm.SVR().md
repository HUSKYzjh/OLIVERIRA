在 Scikit Learn 中有 `LinearSVR` 和 `SVR` 两个类，前者就是使用 SVM 线性方式解决回归问题的类，后者是 SVM 使用核函数方式解决回归问题的类, SVM 解决回归问题的思路和解决分类问题的思路正好是相反的。我们回忆一下，在 Hard Margin SVM 中，我们希望在 Margin 区域中一个样本点都没有，即便在 Soft Margin SVM 中也是希望 **Margin 区域中的样本点越少越好**。

而在 SVM 解决回归问题时，**是希望 Margin 区域中的点越多越好**：