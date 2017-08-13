# Speech Recognition with Deep Recurrent Neural Networks 
[PDF HERE](https://arxiv.org/pdf/1303.5778.pdf)
>Graves, A., Mohamed, A. R., & Hinton, G. (2013, May). Speech recognition with deep recurrent neural networks. In 2013 IEEE international conference on acoustics, speech and signal processing (pp. 6645-6649). IEEE.

## 1. Introduction
神經網路常被拿來處理語音辨識，以往一般結合Hidden Markov Model (HMM)，但由於聲學模型需考慮到語音幀間的長時相關性，近年用Recurrent Neural Network(RNN)或HMM-RNN替代 (因RNN有記憶能力)。此篇旨在探討將RNN加深後成果是否會變好， 此篇也是第一次將deep LSTM的概念應用在語音辨識上，且有顯著效果。
```
HMM:隱藏馬可夫模型 http://www.csie.ntnu.edu.tw/~u91029/HiddenMarkovModel.html#2
```

***
## 2.文獻回顧
### RNN
The output of hidden layer are stored in the memory.
Memory can be considered as another input.
```
speech recognition with deep recurrent neural networks-论文笔记第2部分:
http://blog.csdn.net/thy_2014/article/details/50497822
```
### 長短期記憶人工神經網絡（Long-Short Term Memory, LSTM）
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/LSTM.PNG)

LSTM是一種特殊的RNN，可記憶長期訊息，解決了傳統RNN梯度消失等問題。

LSTM使用memory cells儲存訊息，cell內部決定要保留那些記憶，並決定要輸出哪些訊息。
```
最新语音识别系统和框架深度剖析: http://codecloud.net/17305.html
LSTM和RNN网络教程:https://www.zhihu.com/question/29411132
```
### Bidirectional RNN
傳統RNN只能利用上文的內容，對語音辨識來說下文的內容同樣重要。BRNN使用兩個隱藏層。

結合BRNN與LSTM成為雙向LSTM，可取得大範圍且兩個方向的上下文。

***

## 3. Network Training
此篇專注於end-to-end training的改善

### CTC 鏈結式時間分類算法

Connectionist Temporal Classification是一種改良RNN的模型，接在RNN網絡最後一層用於序列學習。此篇用CTC在input與output序列間產生機率分布，達到不需將output(label)與input (音訊)對應起來就可以訓練。

CTC將發音單元之間混淆或不確定的區域映射到blank symbol( Φ)，最後把blank和預測出的重複符號消除。

e.g. 預測出 "ΦΦcΦaaaΦΦtt"，就對應序列 "cat"，"ccΦaΦΦtΦ"，也對應序列 "cat"
                  
```
[论文]CTC: http://www.jianshu.com/p/8406618e940f
AI浪潮下，语音识别建模技术的演进: http://www.leiphone.com/news/201609/MeknwgR9xf0nf8pc.html
语音识别中的CTC方法的基本原理: https://www.zhihu.com/question/47642307
```


### RNN Transducer
將CTC及RNN的預測結合進一個feed-forward network，作者稱之為RNN Transducer。

此篇RNN Transducer用以下兩種方法做訓練:

1. 用隨機初始weights (實驗中簡稱TRANS)
2. 用pretrained CTC network的weights做初始 (此實驗是pretrain audio training data) (實驗中簡稱PRETRANS)
```
In this work we pretrain the prediction network on the phonetic transcriptions of the audio training data.
```
### 正規化

因RNN易overfit，必須正規化，此篇用:

1. Early stopping : 在每一個Epoch結束時計算validation data的accuracy，當accuracy不再提高時，就停止訓練。
2. Weight noise : 訓練時將Gaussian noise加入network weights，每個training sequence加一次，可簡化神經網路。
```
一個Epoch集為對所有的訓練數據的一輪遍歷
```
***
## 4. Experiment
使用TIMIT 語料資料庫
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/timit.PNG)

### Result
![](https://github.com/jasminehung/Deep-Learning-paper/blob/master/images/result.PNG)

***
## Conclusion
將deep且雙向的LSTM RNN與端對端訓練結合，成為語音辨識最新技術突破。
***

## Future work
+ 擴展到更多字彙的辨識
+ 將deep LSTM結合frequency domain CNN
***

## 參考
+ [Summary of the paper Speech recognition with deep recurrent neural networks](http://wikicoursenote.com/wiki/Graves_et_al.,_Speech_recognition_with_deep_recurrent_neural_networks)

