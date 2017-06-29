# Matching Networks for One Shot Learning (Google DeepMind)
[PDF HERE](https://arxiv.org/pdf/1606.04080.pdf)

本文通过拓展的外部信息加强记忆神经网络的效果，提出了一种针对one-shot学习的神经网络模型-Matching Net (MN).该模型可将一个小的标注集合以及一个未标注的测试样例映射到它对应的标签，在这个过程中避免了对于新的标签类别进行调整的需求。该方法在ImageNet数据集的one-shot准确率从87.6%提升到了93.2%，在Omniglot数据集上的效果从88.0%提升到了93.8%。

### 1. 

此篇合併參數與非參數模型的優點
```
- 參數模型: 简化目标函数为已知形式的算法就称为参数机器学习算法。
通过固定大小的参数集(与训练样本数独立)概况数据的学习模型称为参数模型。
不管你给与一个参数模型多少数据，对于其需要的参数数量都没有影响。

- 非參數模型(non-parametric): 对于目标函数形式不作过多的假设的算法称为非参数机器学习算法。
通过不做假设，算法可以自由的从训练数据中学习任意形式的函数。
当你拥有许多数据而先验知识很少时，非参数学习通常很有用，此时你不需要关注于参数的选取。
如: 决策树(例如CART和C4.5)、SVM、神经网络、Kmeans...
```

本文創新之處有二： 
- 模型设计中，借鉴了当下流行的注意力LSTM，考虑了整个参考集合的贡献； 
- 训练过程中，尽量模拟测试流程，使用小样本构造minibatch。
Matching Net (MN) 该模型可以将一个小的标注集合以及一个未标注的测试样例映射到它对应的标签，在这个过程中避免了对于新的标签类别进行调整的需求。


### 2. Model (本文提出一種非參的方法來解决one-shot學習問題)
![](http://read.html5.qq.com/image?src=forum&q=5&r=0&imgflag=7&imageUrl=http://mmbiz.qpic.cn/mmbiz/G3dAicUK7RSL69ict9U1UsiciaQHSI3hwoZmPVZia8dLgdfPqI8ibCLicR9q8lmP130wC1MvoFDZPEBXYrxkicWicn1pEpA/0?wx_fmt=png)

f:针对支持集合样例的嵌入函数。g:针对testing sample的嵌入函数。用来将图像或者文本表示成向量形式。对于图像相关的任务，一般采用深层卷积神经网络，而对于文本相关的任务，通常直接利用简单的词向量表示。


MN的输入包括长度为k的有标注的支持集合S以及一个未标注的testing sample x，输出为该testing sample对应的类别y。
通过引入attention机制，testing sample的类别输出为支持集合中样例的类别的线性组合：(a为attention kernel)

![](http://read.html5.qq.com/image?src=forum&q=5&r=0&imgflag=7&imageUrl=http://mmbiz.qpic.cn/mmbiz/G3dAicUK7RSL69ict9U1UsiciaQHSI3hwoZmkCRG3iaCFpCxaC4Zgjp8WXO1YNBGMXthvsVZcZNTQtCjV5oRdk224hw/0?wx_fmt=png)

### 2.1.1 注意力模型
得到支持样例以及测试样例的表示之后，我们可以计算向量之间的余弦距离并通过softmax函数来作为attention kernel的实现，如下所示：
![](http://read.html5.qq.com/image?src=forum&q=5&r=0&imgflag=7&imageUrl=http://mmbiz.qpic.cn/mmbiz/G3dAicUK7RSL69ict9U1UsiciaQHSI3hwoZmc9EnZibrDI10X8CordKiaxzliaiblvK4av6NCT2VgEsFqfxX76wsSUrtAA/0?wx_fmt=png)

### 2.2 Training Strategy
MN的参数集合θ包括嵌入函数f和g中的参数。
首先定义T为L在标签集上的分布。根据T抽样出标签集L，例如{cats, dogs}。

随后，根据抽样出来的标签集L抽样产生支持集合S和训练batch B，这些集合都是由已标注的cats或dogs的样例构成。

Matching Net的目标是最大化根据支持集合S预测训练batch B中标签的概率，如下所示：

![](http://read.html5.qq.com/image?src=forum&q=5&r=0&imgflag=7&imageUrl=http://mmbiz.qpic.cn/mmbiz/G3dAicUK7RSL69ict9U1UsiciaQHSI3hwoZmyibIcnoTymlCQRkNGkibwAId5tN4ibbGLEicPn74Jt5sX0utxhNALoYxlA/0?wx_fmt=png)

### 3.1 MANN - Learning to Learn
Meta-learning 一般指的是一種遷移學習(Transfer Learning），透過已有的知識輔助新知識的學習

Neuaral Turing Machine(NTM) 引入带记忆的神经网络去模拟大脑皮质的长时记忆功能，实现用极少量新任务的观测数据进行快速学习。不同于传统神经网络，NTM通过控制器（Controller）对Input/Output向量进行选择性地读写操作，实现与外部记忆矩阵（Memory）进行交互。

### 4
N-way k-shot
```
N: 有幾class。
K: 提供K個labelled example。
L': 保留出來不被train的subset
```

### 4.1.1 Omniglot
这个数据库中有1623个字符，由50种不同的字母表组成的。由20位人員手写了这些字符。

### 4.1.2 ImageNet
+ rand setup
+ dogs setup
+ miniImageNet

參考
+ [http://blog.csdn.net/shenxiaolu1984/article/details/53129937](http://blog.csdn.net/shenxiaolu1984/article/details/53129937)
+ [http://chuansong.me/n/371517551454?jdfwkey=umt172](http://chuansong.me/n/371517551454?jdfwkey=umt172)
+ [投影片](https://www.slideshare.net/KazukiFujikawa/matching-networks-for-one-shot-learning-71257100)
+ [深度:机器如何模仿人类的学习方式?](http://www.sohu.com/a/113603719_114877)
+ [参数和非参数机器学习算法](http://shujuren.org/article/106.html)
+ 
