# Matching Networks for One Shot Learning (Google DeepMind)
[PDF HERE](https://arxiv.org/pdf/1606.04080.pdf)

### 1. 本文創新之處有二： 
- 模型设计中，借鉴了当下流行的注意力LSTM，考虑了整个参考集合的贡献； 
- 训练过程中，尽量模拟测试流程，使用小样本构造minibatch。
Matching Net (MN) 该模型可以将一个小的标注集合以及一个未标注的测试样例映射到它对应的标签，在这个过程中避免了对于新的标签类别进行调整的需求。

### 2. Model
### 2.1.1 注意力模型

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

參考
+ [http://blog.csdn.net/shenxiaolu1984/article/details/53129937](http://blog.csdn.net/shenxiaolu1984/article/details/53129937)
+ [http://chuansong.me/n/371517551454?jdfwkey=umt172](http://chuansong.me/n/371517551454?jdfwkey=umt172)
+ [投影片](https://www.slideshare.net/KazukiFujikawa/matching-networks-for-one-shot-learning-71257100)
+ [深度:机器如何模仿人类的学习方式?](http://www.sohu.com/a/113603719_114877)
