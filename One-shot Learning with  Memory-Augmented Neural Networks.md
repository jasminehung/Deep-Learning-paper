# One-shot Learning with Memory-Augmented Neural Networks

此Memory Neural Networks 用的是external memory，與LSTM、RNN不同，而是有另外一塊memory，不是把memory存在neuron裡的那種。

NTM適合用在有時序關係的預測上。more sophisticated memory access capabilities are more powerful, but the controller requires more training.
Read/Write Head: 記憶體的讀寫頭，相當於pointer ，是要被讀取或被寫入的記憶體的address。


## MANN記憶增強神經網絡(Learning to Learn)
相比於NTM，MANN提出了一種新讀寫更新方法—LRUA（Least Recently Used Access）。有別於 NTM 由信息內容和存儲位置共同決定存儲器讀寫， MANN 的每次讀寫操作只選擇最空閒或最近利用的存儲位置，更為靈活，更適用於無關時序的分類回歸問題。新知識被靈活的存儲訪問，基於新知識和長期經驗可對數據做出精確的推斷。
LRUA用weight W，由神經網路去學W，判斷要選L還是R。

每次讀寫操作只選擇最空閒或最近利用的存儲位置，因此讀寫策略完全由信息內容所決定

One action is that the input is very similar to a previously seen input; in this case, we might want to update whatever we wrote to memory. The other action is that the input isn't similar to a previously seen input; in this case, we don't want to overwrite recent information, so we'll instead write to the least used memory location.

## 實驗
使用Omniglot(1423個class)，Train for 100,000 episodes，每個episodes各有5個隨機挑選的class，並隨意assign 1~5的label，每class有10個instance，共50張圖。
每個episode跟episode間external memory會全部wipe掉。

Test on never-seen classes。

1200class當training，423當testing。一個episode一個class

每個episode跟episode間external memory會全部wipe掉(因task不同，學的是不同的東西)，但仍有跨task的知識incremental learning

external memory處理short-term 記憶與new information

要記很多東西時只需擴充external memory，不須擴充神經網路的parameter

## 參考
+ [Chinese explanation with English slides Youtube](https://www.youtube.com/watch?v=el8rWhkCtUI)
+ [Explanation of
One-shot Learning with Memory-Augmented Neural Networks](https://rylanschaeffer.github.io/content/research/one_shot_learning_with_memory_augmented_nn/main.html)
+ [Korean Slides](https://www.slideshare.net/ssuser06e0c5/metalearning-with-memory-augmented-neural-networks)
+ [類神經網路-Neural Turing Machine](http://cpmarkchang.logdown.com/posts/279710-neural-network-neural-turing-machine)


