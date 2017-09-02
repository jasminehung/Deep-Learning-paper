# An unsupervised hierarchical feature learning framework for one-shot image recognition

### 1. Intro
One-shot recognition task includes data from 
- Target domain : 實際進行分類的domain，包含target categories的資料( each category只有一個training sample)  ->做監督式分類 (常用 Nearest neighbor、Naive Bayesian、SVM...)
- Proir-knowledge domain : 不同於Target domain的data，此篇僅用"unlabled" images ( 模擬人腦的學習 ) -> 做feature learning


此篇的Proir-knowledge domain使用unlabled images，與以往論文有很大不同。
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/target.PNG)

- Proir-knowledge domain用unlabled images來學習的例子-分辨斑馬與馬: 從斑馬資料集中學習出"條紋"這個重要的特徵，此特徵未來也可運用在分辨老虎與豹等等不同類別。

此篇用Hierarchical Dirichlet Process (HDP，階層式狄氏程序)來學習Proir-knowledge domain，HDP-encoder can encode low-level特徵的histograms into higher-level特徵vector





- [Domain Adaptation、One-shot/zero-shot Learning概述](https://kknews.cc/zh-tw/news/3jqr65o.html)
