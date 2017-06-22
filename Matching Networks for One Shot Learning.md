# Matching Networks for One Shot Learning (Google DeepMind)
[PDF HERE](https://arxiv.org/pdf/1606.04080.pdf)

本文创新之处有二： 
- 模型设计中，借鉴了当下流行的注意力LSTM，考虑了整个参考集合的贡献； 
- 训练过程中，尽量模拟测试流程，使用小样本构造minibatch。
Matching Net (MN) 该模型可以将一个小的标注集合以及一个未标注的测试样例映射到它对应的标签，在这个过程中避免了对于新的标签类别进行调整的需求。
