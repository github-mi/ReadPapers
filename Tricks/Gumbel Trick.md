# Gumbel 分布

Gumbel distribution(Generalized Extreme Value distribution Type-I)用于衡量某些分布的采样的最大值(或最小值)的分布。

> 例如，已知某条河流过去十年里的最大水位值，则今年该条河流的最大水位x的分布可能是Gumbel分布。

Gumbel分布的累积分布函数为CDF(cumulative distribution function)：

<p align="center"><img src="svgs/42cca485733c709db9826da555c5b552.svg" align=middle width=169.04516475pt height=22.02199395pt/></p>

# Inverse transform sampling

逆变换采样，在已知任意概率分布的累积分布函数时，可用于从该分布中生成随机样本。

对于随机变量<img src="svgs/cbfb1b2a33b28eab8a3e59464768e810.svg" align=middle width=14.908688849999992pt height=22.465723500000017pt/>，其CDF为<img src="svgs/ac48785c4e77d2ea024e6a116c3875cc.svg" align=middle width=136.6684209pt height=24.65753399999998pt/>，则有随机变量<img src="svgs/b9c8533953a449561e275e36ff127739.svg" align=middle width=75.66203369999998pt height=24.65753399999998pt/>，服从 <img src="svgs/f16cf7b4410e4a15788c128aa491f342.svg" align=middle width=105.16729739999998pt height=24.65753399999998pt/> 分布。

> __Proof__:
> <p align="center"><img src="svgs/e6f09056d11e7d1a6b84d3a4e23969fe.svg" align=middle width=222.9259725pt height=69.8303562pt/></p>

逆变换采样将上面过程反过来进行，从 <img src="svgs/f16cf7b4410e4a15788c128aa491f342.svg" align=middle width=105.16729739999998pt height=24.65753399999998pt/> 中采样 <img src="svgs/6dbb78540bd76da3f1625782d42d6d16.svg" align=middle width=9.41027339999999pt height=14.15524440000002pt/> ，再逆变换 <img src="svgs/3545e9458e9dc0c3c2ccfcdf8b5b40b9.svg" align=middle width=82.98333614999999pt height=26.76175259999998pt/> ，<img src="svgs/f93ce33e511096ed626b4719d50f17d2.svg" align=middle width=8.367621899999993pt height=14.15524440000002pt/> 服从CDF为函数F的概率分布。

> __Proof__:
> <p align="center"><img src="svgs/23cee4b0b2bd9414132a09399fe439de.svg" align=middle width=220.23415425pt height=67.6274511pt/></p>

# Gumbel Max Trick

对于一个分类分布(Categorical distribution)

<p align="center"><img src="svgs/80da4d19c0fade91c545d1ce4a90c80d.svg" align=middle width=209.38744695pt height=16.438356pt/></p>

Gumbel Max trick是一种利用Gumbel分布对Categorical分布进行采样的技巧，采样步骤为：  

1. <img src="svgs/d65512c65ec8e1717087a6e76c7e30c0.svg" align=middle width=140.1008664pt height=24.65753399999998pt/> 采样 <img src="svgs/ed705ef0ff14d248a627e57d4aeb82cc.svg" align=middle width=74.5760895pt height=14.15524440000002pt/> (用于下一步Gumbel采样)
2. <img src="svgs/8832dbb8ace2f9ae9e50f2e2a340a363.svg" align=middle width=218.3947458pt height=24.65753399999998pt/>，则<img src="svgs/c7a6b14061ec17f09f80314e15ab9c6a.svg" align=middle width=171.66978509999998pt height=27.6567522pt/>是标准Gumbel分布中的采样
3. <img src="svgs/de654efd9587bf744a3a2c68bce45bc6.svg" align=middle width=149.44635419999997pt height=27.100362300000015pt/>是服从Categorical分布的，<img src="svgs/9fc20fb1d3825674c6a279cb0d5ca636.svg" align=middle width=14.045887349999989pt height=14.15524440000002pt/>是<img src="svgs/fb7276301b30b0ad84054b52f14d0628.svg" align=middle width=14.021211599999992pt height=14.15524440000002pt/>对应的logits(即<img src="svgs/ff78d6f07bfe340dfe5eed58d9e4ad6e.svg" align=middle width=112.5250137pt height=24.65753399999998pt/>)

> __Proof:__
> 令 <img src="svgs/0e3e3989a8509b84906836518a05fcf2.svg" align=middle width=94.18838384999998pt height=24.65753399999998pt/>，则 <img src="svgs/02ab12d0013b89c8edc7f0f2662fa7a9.svg" align=middle width=10.58699729999999pt height=20.221802699999984pt/>是服从 <img src="svgs/bf331ae087cc8580448f66d3f95e6677.svg" align=middle width=69.34493444999998pt height=24.65753399999998pt/> 分布的，需要证明：
> <p align="center"><img src="svgs/4d5790c180778d6180f75df05ea6e72f.svg" align=middle width=251.43161835pt height=47.4432255pt/></p> 证明过程：
> <p align="center"><img src="svgs/8dff4d52980dbc1959cc0dc96a3dc5f9.svg" align=middle width=538.1086953pt height=97.44363915pt/></p> 令 <img src="svgs/9b15358caff87cfbaae27e5c07099460.svg" align=middle width=61.407952649999984pt height=26.17730939999998pt/> ，则 <img src="svgs/3df80fa9a3d6efeddeb6042d78970172.svg" align=middle width=87.54656789999999pt height=24.65753399999998pt/>， <img src="svgs/a3c3d8178764ded66839fc2598ececd3.svg" align=middle width=89.83634715pt height=24.65753399999998pt/>
> <p align="center"><img src="svgs/8fab83ba71d4e20c5abbedf2fc9bb1e9.svg" align=middle width=519.35163885pt height=200.3743434pt/></p> 得证。

# Gumbel Softmax Trick

Gumbel Max Trick 得到的是Categorical分布的离散采样<img src="svgs/459ed7191ad1f26edca272778d348f7c.svg" align=middle width=105.06438854999999pt height=24.65753399999998pt/>

由于有argmax操作，存在采样操作梯度不可导的问题。Gumbel Softmax Trick采用softmax函数得到一个K维的概率向量：
<p align="center"><img src="svgs/24450bf266668c3500ac54bf65e48960.svg" align=middle width=215.7567918pt height=49.315569599999996pt/></p>

# 参考资料

- <https://www.zybuluo.com/pearl3344/note/878835>
- [The Concrete Distribution: A Continuous Relaxation of Discrete Random Variables](https://arxiv.org/abs/1611.00712)(有gumbel softmax 分布的推导)
- [Categorical Reparameterization with Gumbel-Softmax](https://arxiv.org/abs/1611.01144)
