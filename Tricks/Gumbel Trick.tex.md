# Gumbel 分布

Gumbel distribution(Generalized Extreme Value distribution Type-I)用于衡量某些分布的采样的最大值(或最小值)的分布。

> 例如，已知某条河流过去十年里的最大水位值，则今年该条河流的最大水位x的分布可能是Gumbel分布。

Gumbel分布的累积分布函数为CDF(cumulative distribution function)：

$$G(x;\mu,\beta) = e^{-e^{-(x-\mu)/\beta}}$$

# Gumbel Max Trick

对于一个分类分布(Categorical distribution)

$$Y \sim Categorical(\pi_1,\dots,\pi_K)$$

Gumbel Max trick是一种利用Gumbel分布对Categorical分布进行采样的技巧，采样步骤为：  

1. $U \sim Uniform(0,1)$ 采样 $u_1,\dots,u_K$ (用于下一步Gumbel采样)
2. $Z = -\ln(-\ln(U)) \sim G(z;0,1)$，则$\{z_i = -\ln(-\ln(u_i))\}_{i=1}^K$是标准Gumbel分布中的采样
3. $Y = \argmax_i (x_i + z_i)$是服从Categorical分布的，$x_i$是$\pi_i$对应的logits

> __Proof:__
> 令 $t_i = (x_i + z_i)$，则 $t_i$是服从 $G(t;x_i,1)$ 分布的，需要证明：
> $$\int_{t_i} P(t_i) \cdot \prod_{j \neq i} Pr(t_j < t_i) = \pi_i$$
> $$
\int_{t_i} P(t_i) \cdot \prod_{j \neq i} Pr(t_j < t_i) = \int_{-\infty}^{+\infty} e^{-(t_i - x_i) - e^{-(t_i - x_i)}} \cdot \prod_{j \neq i} e^{-e^{-(t_i - x_j)}} dt_i \\
= \int_{-\infty}^{+\infty} e^{-t_i + x_i - e^{-t_i} \cdot \sum_j e^{x_j}} dt_i
$$
> 令 $w = e^{-t_i}$ ，则 $t_i = -\ln(w)$， $w \in (0,+\infty)$
> 
