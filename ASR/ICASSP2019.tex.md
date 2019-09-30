# Improving noise robustness of automatic speech recognition via parallel data and teacher-student learning

这篇论文是Amazon的工作，一作是在Amazon实习。

论文想做的事情是提升在噪声环境下(Amazon有Echo助手，所以针对的是家庭多媒体噪声)ASR的识别率。

使用了800h带文本的语音+8000h不带文本的语音。

论文的思想很简单，先用800h带文本的语音训练Teacher模型，然后使用8000h不带文本的语音来训练Student模型。Student输入加噪后的语音，预测的目标是Teacher输入干净语音的预测结果的分布(软标签)。示意图如下：

![](E:\Github\ReadPapers\ASR\png\ICASSP2019_1.png)

Logits Selection是指Teacher出来的Logits只取topk，并调节temperature。

实验发现Logits取top 20，temperature为2，不带文本数据量为6倍时效果最好，并且SDT会有进一步提升。

![1569326871686](E:\Github\ReadPapers\ASR\png\ICASSP2019_2.png)

# Knowledge Distillation Using Output Errors for Self-attention End-to-end Models

这篇论文是三星的工作，想做的事情是在不损失性能的情况下进行模型压缩，感觉侧重点是在模型压缩方面。

这篇工作感觉比较solid，网络结果使用Transformer，数据集使用LibriSpeech。





# Read List

- [x] [Improving noise robustness of automatic speech recognition via parallel data and teacher-student learning](https://arxiv.org/abs/1901.02348)
- [x] [Knowledge Distillation Using Output Errors for Self-attention End-to-end Models](https://ieeexplore.ieee.org/abstract/document/8682775/)
- [x] [Unsupervised Data Augmentation for Consistency Training](https://arxiv.org/abs/1904.12848)