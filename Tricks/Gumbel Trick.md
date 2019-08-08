# Gumbel 分布

Gumbel distribution(Generalized Extreme Value distribution Type-I)用于衡量某些分布的采样的最大值(或最小值)的分布。

> 例如，已知某条河流过去十年里的最大水位值，则今年该条河流的最大水位x的分布可能是Gumbel分布。

Gumbel分布的累积分布函数为CDF(cumulative distribution function)：

<p align="center"><img src="svgs/42cca485733c709db9826da555c5b552.svg" align=middle width=169.04516475pt height=22.02199395pt/></p>

# Gumbel Max Trick

对于一个分类分布(Categorical distribution)

<p align="center"><img src="svgs/80da4d19c0fade91c545d1ce4a90c80d.svg" align=middle width=209.38744695pt height=16.438356pt/></p>

Gumbel Max trick是一种利用Gumbel分布对Categorical分布进行采样的技巧，采样步骤为：  

1. <img src="svgs/d65512c65ec8e1717087a6e76c7e30c0.svg" align=middle width=140.1008664pt height=24.65753399999998pt/> 采样 <img src="svgs/ed705ef0ff14d248a627e57d4aeb82cc.svg" align=middle width=74.5760895pt height=14.15524440000002pt/> (用于下一步Gumbel采样)
2. <img src="svgs/8832dbb8ace2f9ae9e50f2e2a340a363.svg" align=middle width=218.3947458pt height=24.65753399999998pt/>，则<img src="svgs/c7a6b14061ec17f09f80314e15ab9c6a.svg" align=middle width=171.66978509999998pt height=27.6567522pt/>是标准Gumbel分布中的采样
3. <img src="svgs/dda3522dbf5e8bce13675dd805752fde.svg" align=middle width=101.44866599999999pt height=24.65753399999998pt/>是服从Categorical分布的，<img src="svgs/9fc20fb1d3825674c6a279cb0d5ca636.svg" align=middle width=14.045887349999989pt height=14.15524440000002pt/>是<img src="svgs/fb7276301b30b0ad84054b52f14d0628.svg" align=middle width=14.021211599999992pt height=14.15524440000002pt/>对应的logits

> __Proof:__
> 令 <img src="svgs/0e3e3989a8509b84906836518a05fcf2.svg" align=middle width=94.18838384999998pt height=24.65753399999998pt/>，则 <img src="svgs/02ab12d0013b89c8edc7f0f2662fa7a9.svg" align=middle width=10.58699729999999pt height=20.221802699999984pt/>是服从 <img src="svgs/bf331ae087cc8580448f66d3f95e6677.svg" align=middle width=69.34493444999998pt height=24.65753399999998pt/> 分布的，需要证明：
> <p align="center"><img src="svgs/c93ad60507f312d1e4d0f807795a0149.svg" align=middle width=211.13758875pt height=44.383808699999996pt/></p>
> <img src="svgs/da79ea4fd0aac9d5be10e808310661ef.svg" align=middle width=207.36960584999997pt height=26.48417309999999pt/>
