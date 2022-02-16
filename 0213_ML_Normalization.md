# Normalization
## 1 Why Normalization

1. **从logistics regression说起**：由于weights初始化都在差不多的值域范围内，如果特征值域相差较大，损失函数的求导会受到值域更大的特征的主导，因此需要对特征进行标准化处理。

    （相较之下，一些其他的机器学习算法，例如树模型，由于降低loss的手段是找到信息熵下降分隔方式loss与特征值域无关，无需进行标准化。）

2. **神经网络->lr的层层叠加**：理解了lr为什么需要标准化就比较好理解nn的标准化方式，由于每层的输出都是下一层的输入，当weights更新后，中间层的输出分布变化较大（Internal Covariate Shift），因此需要对每层输入输出进行标准化。

<br/>

## 2 Normalization 算法
从标准化的出发点而言，期待的结果是经过标准化算法后输入向量的各个值都被放缩到一个相近的范围。假设特征值均服从高斯分布，那么一种手段就是将各个特征放缩到同样均值方差的分布，即：

$$x'=\frac{x - \mu}{\sigma}$$

这个方式对于lr来说没有任何问题，但是放到nn里就不是太合理了：中间层即是输入也是**输出**，一旦采取上面的标准化方式，意味着每一层的输出节点都必须服从一样的分布，对于神经网络的表达能力将是一种限制。因此有了以下变体：

$$x'=\gamma * \frac{x - \mu}{\sigma} + \beta$$

<br/>

### 2.1 BatchNorm：纵向标准化(Google, 2015)


BatchNorm的Batch就是Minibatch的Batch，不难理解，就是按照对若干样本的同一个特征进行标准化。(下面是一个minibatch的例子，字母代表不同特征，数字代表不同样本，bn可以理解成纵向也就是样本维度的标准化)。


    [[a1,  b1,  c1, d1]

     [a2,  b2,  c2, d2]

     [a3,  b3,  c3, d3]]


bn的问题在于当batchsize较小或是不同batch的分布差异较大时结果相对不可用。

<br/>

### 2.2 LayerNorm：横向标准化

ln在特征维度进行标准化，避免受到batch的影响，但是可解读性变差。

<br/>

# Ref
https://zhuanlan.zhihu.com/p/54530247

https://zhuanlan.zhihu.com/p/54530247