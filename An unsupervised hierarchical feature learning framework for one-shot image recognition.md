# An unsupervised hierarchical feature learning framework for one-shot image recognition

### 1. 
One-shot recognition task includes data from 
- Target domain : 實際進行分類的domain，包含target categories的資料( each category只有一個training sample)  ->做監督式分類
- Proir-knowledge domain : 不同於Target domain的data，此篇僅用"unlabled" images ( 模擬人腦的學習) -> 做feature learning

![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/target.PNG)

- 用unlabled images來學習的例子-分辨斑馬與馬: 從斑馬資料集中學習出"條紋"這個重要的特徵，此特徵未來也可運用在分辨老虎與豹等等不同類別。
