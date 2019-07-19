<!-- TOC -->

- [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](#bert-pre-training-of-deep-bidirectional-transformers-for-language-understanding)
- [MASS: Masked Sequence to Sequence Pre-training for Language Generation](#mass-masked-sequence-to-sequence-pre-training-for-language-generation)
- [XLNet: Generalized Autoregressive Pretraining for Language Understanding](#xlnet-generalized-autoregressive-pretraining-for-language-understanding)
- [参考资料](#参考资料)
- [Read List](#read-list)

<!-- /TOC -->

# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

# MASS: Masked Sequence to Sequence Pre-training for Language Generation

# XLNet: Generalized Autoregressive Pretraining for Language Understanding

2019年6月出现在[arxiv](https://arxiv.org/abs/1906.08237)上，作者主要来自CMU和Google Brain。  

作者放出了预训练的模型和代码：<https://github.com/zihangdai/xlnet>  

这篇论文借鉴了Transformer-XL的思想，提出了新的预训练语言模型XLNet，在20项NLP任务上全面超越Bert，其中18项做到了state-of-the-art的结果。(question answering, naturallanguage inference, sentiment analysis, and document ranking)  

> NLP的套路一般分为两步走，首先用大量的无标签的文本语料预训练出一个模型，然后在完成下游任务时对预训练的模型进行finetune。

无监督预训练模型的方法可以分为两大类：autoregressive (AR) 和 autoencoding (AE)。

- AR旨在使用自回归模型建立文本语料的概率分布。  
具体来说就是给定一段文本序列 <img src="svgs/4dfed65fc01f334683c73bd5faad8339.svg" align=middle width=119.88715529999997pt height=24.65753399999998pt/> ，AR会将likelihood拆成前向概率连乘 <img src="svgs/2473b3271c84af8da5416cc9988c6b02.svg" align=middle width=169.04093744999997pt height=32.256008400000006pt/> 或者反向概率连乘 <img src="svgs/aad61e222554548a3630c1aadcfe93ea.svg" align=middle width=172.02206999999999pt height=31.36100879999999pt/> 。  

- AE

# 参考资料

- [nlp中的词向量对比：word2vec/glove/fastText/elmo/GPT/bert](https://www.jianshu.com/p/d0d5a828bcaa)
- [自然语言处理中的语言模型预训练方法（ELMo、GPT和BERT）](https://www.cnblogs.com/robert-dlut/p/9824346.html)

# Read List

- [ ] [ELMo](https://arxiv.org/abs/1802.05365)
- [ ] [GPT]()
- [ ] [Bert](https://arxiv.org/abs/1810.04805)
- [ ] [MASS](https://arxiv.org/abs/1905.02450)
- [x] [XLNet](https://arxiv.org/abs/1906.08237)
