# Meta-learning with memory-augmented neural networks (2016)
[PDF HERE](https://arxiv.org/abs/1605.06065)

## Intro
此Memory Neural Networks 用的是external memory，與LSTM、RNN不同，而是有另外一塊memory，不是把memory存在neuron裡的那種。

要記很多東西時只需擴充external memory，不須擴充神經網路的parameter。

## NTM
NTM適合用在有時序關係的預測上。more sophisticated memory access capabilities are more powerful, but the controller requires more training.
Read/Write Head: 記憶體的讀寫頭，相當於pointer ，是要被讀取或被寫入的記憶體的address。

## Omniglot
使用Omniglot(1423個class)，Train for 100,000 episodes，每個episodes各有5個隨機挑選的class，並隨意assign 1~5的label，每class有10個instance，共50張圖。

1200class當training，423當testing。一個episode一個class
每個episode跟episode間external memory會全部wipe掉(因task不同，學的是不同的東西)，但仍有跨task的知識incremental learning
external memory處理short-term 記憶與new information

Test on never-seen classes。

## 參考
+ [深度學習的新方向 One-shot learning](http://tzuching1.weebly.com/blog/-one-shot-learning)
+ [深度：機器如何模仿人類的學習方式？](https://www.hksilicon.com/articles/1170358)
+ [Explanation of
One-shot Learning with Memory-Augmented Neural Networks](https://rylanschaeffer.github.io/content/research/one_shot_learning_with_memory_augmented_nn/main.html)
+ [中文解說影片](https://www.slideshare.net/KatyLee4/meta-learning-with-memory-augmented-neural-network)
+ [韓文投影片](https://www.slideshare.net/ssuser06e0c5/metalearning-with-memory-augmented-neural-networks)
+ [類神經網路-Neural Turing Machine](http://cpmarkchang.logdown.com/posts/279710-neural-network-neural-turing-machine)
