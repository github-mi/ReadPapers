# Optimal Completion Distillation for Sequence Learning

这篇论文是Google的工作，作者是Sara Sabour。  
在2018年10月这篇论文刚出来的时候在LibriSpeech上获得了state-of-the-art的结果，WER在clean测试集上为4.5%，在other测试集上13.3%。不过半年之后就被[SpecAugment](https://arxiv.org/abs/1904.08779)给干趴下了，clean上做到2.8%，other上做到6.8%。

这篇论文对优化目标做了改进，一般seq2seq模型都是使用Maximum Likelihood Estimation(MLE)来进行优化，将串序列的likelihood拆为条件概率连乘$\$

# Read List

- [X] [Optimal Completion Distillation for Sequence Learning](https://arxiv.org/abs/1810.01398)
