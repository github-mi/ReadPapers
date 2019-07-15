> 提示：GitHub无法正常显示公式，可以使用[GitHub with MathJax](https://chrome.google.com/webstore/detail/mathjax-plugin-for-github/ioemnmodlmafdkllaclgeombjnmnbima)插件来解决此问题

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
具体来说就是给定一段文本序列 $x = (x_1,\cdots,x_T)$ ，AR会将likelihood拆成前向概率连乘 $p(x) = \prod_{t=1}^T p(x_t \mid \mathbf{x}_{<t})$ 或者反向概率连乘 $p(x) = \prod_{t=T}^1 p(x_t \mid \mathbf{x}_{>t})$ 。  

- AE test

# 参考资料

- [nlp中的词向量对比：word2vec/glove/fastText/elmo/GPT/bert](https://www.jianshu.com/p/d0d5a828bcaa)
- [自然语言处理中的语言模型预训练方法（ELMo、GPT和BERT）](https://www.cnblogs.com/robert-dlut/p/9824346.html)

# Read List

- [ ] [ELMo](https://arxiv.org/abs/1802.05365)
- [ ] [GPT]()
- [ ] [Bert](https://arxiv.org/abs/1810.04805)
- [ ] [MASS](https://arxiv.org/abs/1905.02450)
- [x] [XLNet](https://arxiv.org/abs/1906.08237)
