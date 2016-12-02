# Speech Recognition with Deep Recurrent Neural Networks 
[PDF HERE](https://arxiv.org/pdf/1303.5778.pdf)
>Graves, A., Mohamed, A. R., & Hinton, G. (2013, May). Speech recognition with deep recurrent neural networks. In 2013 IEEE international conference on acoustics, speech and signal processing (pp. 6645-6649). IEEE.

##1. Introduction
神經網路常被拿來處理語音辨識，以往一般結合Hidden Markov Model (HMM)，但由於聲學模型需考慮到語音幀間的長時相關性，近年用Recurrent Neural Network(RNN)或HMM-RNN替代 (因RNN有記憶能力)。此篇旨在探討將RNN加深後成果是否會變好， 此篇也是第一次將deep LSTM的概念應用在語音辨識上，且有顯著效果。
```
HMM:隱藏馬可夫模型 http://www.csie.ntnu.edu.tw/~u91029/HiddenMarkovModel.html#2
```

***

##2.
***

##3. Network Training

###RNN Transducer
將CTC及RNN的預測結合進一個feed-forward network，作者稱之為RNN Transducer。

此篇RNN Transducer用以下兩種方法做訓練:

1. 用隨機初始weights (實驗中簡稱TRANS)
2. 用pretrained CTC network的weights做初始 (此實驗是pretrain audio training data) (實驗中簡稱PRETRANS)
```
In this work we pretrain the prediction network on the phonetic transcriptions of the audio training data.
```
###正規化

因RNN易overfit，必須正規化，此篇用:

1. Early stopping : 在每一個Epoch結束時計算validation data的accuracy，當accuracy不再提高時，就停止訓練。
2. Weight noise : 訓練時將Gaussian noise加入network weights，每個training sequence加一次，可簡化神經網路。
```
一個Epoch集為對所有的訓練數據的一輪遍歷
```
***
##4. Experiment
使用TIMIT 語料資料庫
***

## Conclusion
將deep且雙向的LSTM RNN與端對端訓練結合，成為語音辨識最新技術突破。
***

## Future work
+ 擴展到更多字彙的辨識
+ 將deep LSTM結合frequency domain CNN
***
##參考
+ [Summary of the paper Speech recognition with deep recurrent neural networks](http://wikicoursenote.com/wiki/Graves_et_al.,_Speech_recognition_with_deep_recurrent_neural_networks)
+[]()
