#Compressing Neural Networks with the Hashing Trick 
[PDF HERE](http://www.jmlr.org/proceedings/papers/v37/chenc15.pdf)

[Code Download](http://www.cse.wustl.edu/~wenlinchen/project/HashedNets/index.html)
>Chen, W., Wilson, J. T., Tyree, S., Weinberger, K. Q., & Chen, Y. (2015). Compressing neural networks with the hashing trick. CoRR, abs/1504.04788.

## HashedNets


行動裝置記憶體小，無法容納越來越大的深度學習模型，
此篇提出一種新的神經網絡架構:HashedNets，可大大減少模型大小和記憶體需求。
先前研究指出神經網路中學到的weights 有時候是冗餘的，HashedNets 利用這個特性創建使用虛擬連接的神經網絡，有驚人的結果。
HashedNets使用低成本的 hash function來將連接權重分組到hash buckets中，同一bucket內共享一個參數值。使用hashing trick來分配隨機權重共享，各connection共享的權重由 hash function 決定(使用open source的xxHash)。而不需用另個matrix記錄誰對映到誰。
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/hashnet.PNG)

Vi: 第i層的權重矩陣

此研究維持V大小不變，但用weight sharing減少他的effective memory footprint 。

24 weights stored in the matrices V1 and V2 are reduced to only six real values in w1 and w2。


```
xxhash code: https://code.google.com/archive/p/xxhash
xxhash產生器 https://asecuritysite.com/encryption/xxHash
```

## Result
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/hashresult.PNG)

## 參考
+ [Deep Compression and EIE-Song Han](http://web.stanford.edu/class/ee380/Abstracts/160106-slides.pdf)
+ [Deep Compression and EIE-Song Han的影片](https://www.youtube.com/watch?v=CrDRr2fxbsg)
+ [【论文阅读】Deep Compression: Compressing Deep Neural Networks with Pruning, Trained Quantization and Huffman coding](http://blog.csdn.net/cyh_24/article/details/51708469)
