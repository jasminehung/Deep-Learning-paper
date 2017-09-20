## Human-level concept learning through probabilistic program induction

[PDF HERE](https://pdfs.semanticscholar.org/2307/8c79c0fc425653aeafcee2ddd01210254658.pdf)

[slides](http://davidnagy.web.elte.hu/eloadas/kiseloadas/BPL_brendenlake_science_journalclub_WIGNER.pdf)

[作者提供的code](https://github.com/brendenlake/omniglot)

[demo code of a baseline model using Modified Hausdorff Distance](https://github.com/llSourcell/One-Shot-Learning-Demo)


本篇提出Bayesian Program Learning (BPL)架構，比起deep learning，BPL不依賴大量數據且對於少量訓練樣本之學習效果佳，可達到人類水平。

BPL架構:利用隨機程序模型來呈現概念結合Bayesian過程，尋找最可能產生當前看到的圖像的原型

此篇針對手寫文字的實驗，BPL模型學習的數據量與人類完全相同-僅一個(one-shot)，BPL模型取得了與人類相似的成績。



### 補充:
[生成模型generative model和判别模型discriminative model](http://blog.csdn.net/danieljianfeng/article/details/41896323)

[如何评价《Science》封面文章《通过概率规划归纳的人类层次概念学习》](https://www.zhihu.com/question/38440539)
