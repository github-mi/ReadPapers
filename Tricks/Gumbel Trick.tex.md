<!-- TOC -->

- [Gumbel 分布](#gumbel-分布)
- [Inverse transform sampling](#inverse-transform-sampling)
- [Gumbel Max Trick](#gumbel-max-trick)
- [Gumbel Softmax Trick](#gumbel-softmax-trick)
- [参考资料](#参考资料)

<!-- /TOC -->
# Gumbel 分布

Gumbel distribution(Generalized Extreme Value distribution Type-I)用于衡量某些分布的采样的最大值(或最小值)的分布。

> 例如，已知某条河流过去十年里的最大水位值，则今年该条河流的最大水位x的分布可能是Gumbel分布。

Gumbel分布的累积分布函数为CDF(cumulative distribution function)：

$$G(x;\mu,\beta) = e^{-e^{-(x-\mu)/\beta}}$$

# Inverse transform sampling

逆变换采样，在已知任意概率分布的累积分布函数时，可用于从该分布中生成随机样本。

对于随机变量$X$，其CDF为$F(x)=Pr(X \le x)$，则有随机变量$Y=F(X)$，服从 $Uniform(0,1)$ 分布。

> __Proof__:
> $$
\begin{aligned}
Pr(Y \le x) &= Pr(F(X) \le x)\\
&= Pr(X \le F^{-1}(x))\\
&= F(F^{-1}(x)) = x
\end{aligned}
$$

逆变换采样将上面过程反过来进行，从 $Uniform(0,1)$ 中采样 $u$ ，再逆变换 $z = F^{-1}(u)$ ，$z$ 服从CDF为函数F的概率分布。

> __Proof__:
> $$
\begin{aligned}
Pr(Z \le x) &= Pr(F^{-1}(U) \le x)\\
&= Pr(U \le F(x))\\
&= F(x)
\end{aligned}
$$

# Gumbel Max Trick

对于一个分类分布(Categorical distribution)

$$Y \sim Categorical(\pi_1,\dots,\pi_K)$$

Gumbel Max trick是一种利用Gumbel分布对Categorical分布进行采样的技巧，采样步骤为：  

1. $U \sim Uniform(0,1)$ 采样 $u_1,\dots,u_K$ (用于下一步Gumbel采样)
2. $Z = -\ln(-\ln(U)) \sim G(z;0,1)$，则$\{z_i = -\ln(-\ln(u_i))\}_{i=1}^K$是标准Gumbel分布中的采样
3. $Y = \underset{i} {\mathrm{argmax}} (x_i + z_i)$是服从Categorical分布的，$x_i$是$\pi_i$对应的logits(即$x_i = ln(\pi_i)+C$)

> __Proof:__
> 令 $t_i = (x_i + z_i)$，则 $t_i$是服从 $G(t;x_i,1)$ 分布的，需要证明：
> $$
\int_{-\infty}^{+\infty} \prod_{j \neq i} Pr(t_j < t_i) \cdot P(t_i) dt_i = \pi_i $$ 证明过程：
> $$
\begin{aligned} \int_{-\infty}^{+\infty} \prod_{j \neq i} Pr(t_j < t_i) \cdot P(t_i) dt_i &= \int_{-\infty}^{+\infty} e^{-(t_i - x_i) - e^{-(t_i - x_i)}} \cdot \prod_{j \neq i} e^{-e^{-(t_i - x_j)}} dt_i \\
&= \int_{-\infty}^{+\infty} e^{-t_i + x_i - e^{-t_i} \cdot \sum_j e^{x_j}} dt_i \end{aligned} $$ 令 $w = e^{-t_i}$ ，则 $t_i = -\ln(w)$， $w \in (0,+\infty)$
> $$
\begin{aligned} \int_{-\infty}^{+\infty} \prod_{j \neq i} Pr(t_j < t_i) \cdot P(t_i) dt_i &= \int_{-\infty}^{+\infty} e^{-t_i + x_i - e^{-t_i} \cdot \sum_j e^{x_j}} dt_i \\
&= \int_{+\infty}^{0} w \cdot e^{x_i} \cdot e^{- w \cdot \sum_j e^{x_j}} \frac {-dw} {w} \\
&= \frac {e^{x_i}} {\sum_j e^{x_j}} \cdot \int_{+\infty}^{0} e^{- w \cdot \sum_j e^{x_j}} d(-w\cdot \sum_j e^{x_j}) \\
&= \frac {e^{x_i}} {\sum_j e^{x_j}} = \pi_i \end{aligned}$$ 得证。

# Gumbel Softmax Trick

Gumbel Max Trick 得到的是Categorical分布的离散采样$y \in \{1,\dots,K\}$

由于有argmax操作，存在采样操作梯度不可导的问题。Gumbel Softmax Trick采用softmax函数得到一个K维的概率向量：
$$
\vec{y} = \left[\frac {e^{t_1 / \tau}} {\sum_j e^{t_j / \tau}}, \dots, \frac {e^{t_K / \tau}} {\sum_j e^{t_j / \tau}} \right]
$$

# 参考资料

- <https://www.zybuluo.com/pearl3344/note/878835>
- [The Concrete Distribution: A Continuous Relaxation of Discrete Random Variables](https://arxiv.org/abs/1611.00712)(有gumbel softmax 分布的推导)
- [Categorical Reparameterization with Gumbel-Softmax](https://arxiv.org/abs/1611.01144)
