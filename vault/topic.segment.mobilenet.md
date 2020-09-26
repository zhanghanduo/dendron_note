---
id: 34bbc865-ff6e-41d8-8c5c-70c6b37ca3c1
title: Mobilenet
desc: ''
updated: 1601113882598
created: 1601113882598
stub: true
---
# Mobilenet

### Meta Data
- #citekey: _howardMobileNetsEfficientConvolutional2017_
- [[[[Howard, Andrew G.]], [[Zhu, Menglong]], [[Chen, Bo]], [[Kalenichenko, Dmitry]], [[Wang, Weijun]], [[Weyand, Tobias]], et al.]] #authors
- [[2017]] #issued
- #title MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications
- #topic: [[Efficient Redesign of DCNNs]]  #Efficient [[Segmentation]] [[Depthwise Separable Convolution]] [[DSConv]] [[Pointwise Conv]]
### **Abstract**:
  -  MobileNets are based on a **streamlined** architecture that uses [[Depthwise Separable Convolution]] to build light weight deep neural networks.
      - Two global hyperparamters to allow model builder choose the right sized model.
      - Based on reviews, the performance of MobileNet is apparent on **CPUs**.
  
### Standard Conv
 - **Parametrization**: Conv kernel $ \mathbf{K} $ of size $ D_K \times D_K \times {M}\times{N} $  where $ D_K $ is the spatial dimension of the kernel, $ M $ no. of input channels, $ N $ no. of output channels.
 - The output **feature map** assuming stride 1 and padding computed as:
     - $ \mathbf{G}_{k,l,n}=\sum\limits_{i,j,m,n}\mathbf{K}_{i,j,m}\cdot\mathbf{F}_{k+i-1,l+j-1,m} $   where $\mathbf{K} $ is conv kernel of size $ D_K \times D_K \times {M} $ where the $ m_{th} $ filter in $ \hat{\mathbf{K}} $ is applied to the $ m_{th} $ channel in $ \mathbf{F} $ to produce the 
 - ![https://remnote-user-data.s3.amazonaws.com/B_-ajXc9wGIKey3ZocWiE6FCr8IFHndEXzSSSh7xRuEiAPkHj1in3rUYm46JBWWQPQAIbive-qAX84DG-WikxI6K1-jixfFJEMqnzj-oqfaaO507lds14S_r8294-6LD](https://remnote-user-data.s3.amazonaws.com/B_-ajXc9wGIKey3ZocWiE6FCr8IFHndEXzSSSh7xRuEiAPkHj1in3rUYm46JBWWQPQAIbive-qAX84DG-WikxI6K1-jixfFJEMqnzj-oqfaaO507lds14S_r8294-6LD)
  
### Depthwise Separable Convolution  ([[DSConv]])
  - Reduce computation and model size drastically
  - Factorize a standard conv into a [[Depthwise Convolution]] and a $ 1\times 1 $ conv (called [[Pointwise Conv]])
  - Computation cost: $  $$D_K \cdot D_K\cdot M \cdot D_F \cdot D_F + M \cdot N \cdot D_F \cdot D_F $
  - **Depthwise Convolution**: applies a single filter to each input channel. (**Single filter** for each input channel)
      - $ \hat{\mathbf{G}}_{k,l,m}=\sum\limits_{i,j}\hat{\mathbf{K}}_{i,j,m}\cdot\mathbf{F}_{k+i-1,l+j-1,m} $   where $ \hat{\mathbf{K}} $ is depthwise conv kernel of size $ D_K \times D_K \times {M} $ where the $ m_{th} $ filter in $ \hat{\mathbf{K}} $ is applied to the $ m_{th} $ channel in $ \mathbf{F} $ to produce the $ m_{th} $ channel of the filtered output feature map $ \hat{\mathbf{G}} $.
      - Efficient with computation cost: $ D_K \cdot D_K\cdot M \cdot D_F \cdot D_F $ 
      - But only filter input channels without combining them to create new features.
      - ![https://remnote-user-data.s3.amazonaws.com/ith1V3pjj0bCVnUBm55ksoYBkn-C22rW0D4PhODElclSc5OPEl9PZSH5s5-WAmpRSKpANzjTKhdlH97H0f0gSGOmXkaD-6QuoP78M5JuyyWjwFndvXDf0WJ4f4ZXj3wD](https://remnote-user-data.s3.amazonaws.com/ith1V3pjj0bCVnUBm55ksoYBkn-C22rW0D4PhODElclSc5OPEl9PZSH5s5-WAmpRSKpANzjTKhdlH97H0f0gSGOmXkaD-6QuoP78M5JuyyWjwFndvXDf0WJ4f4ZXj3wD)  
  - **Pointwise Conv**: applies a $ 1\times 1 $ conv to linearly ^^combine^^ the outputs of [[Depthwise Convolution]] 
      - ![https://remnote-user-data.s3.amazonaws.com/nZ1utm3m2loE51DLKCzcf6057y2SzQNDeSAEAYOM0RlvuTneWBb63uR5fCjCOxdreJTY0wWrB0iCA8NYOSW7TW-OoA0rf8uQWGsBcVsbY4l2UQ4-NaV3B6xkC6obp-An](https://remnote-user-data.s3.amazonaws.com/nZ1utm3m2loE51DLKCzcf6057y2SzQNDeSAEAYOM0RlvuTneWBb63uR5fCjCOxdreJTY0wWrB0iCA8NYOSW7TW-OoA0rf8uQWGsBcVsbY4l2UQ4-NaV3B6xkC6obp-An)  
  - ![https://remnote-user-data.s3.amazonaws.com/R0BZqYTinw6UTzNpZVfRcl6SVXrm1C8BHdBOAj05K7Vz04OPigkLtx8WENK9GAo060EFFF8a26v71CxGFy-qaezInGDjDycS4wRpo2K9hjQScsoNJ0H0CUAY345YTnTm](https://remnote-user-data.s3.amazonaws.com/R0BZqYTinw6UTzNpZVfRcl6SVXrm1C8BHdBOAj05K7Vz04OPigkLtx8WENK9GAo060EFFF8a26v71CxGFy-qaezInGDjDycS4wRpo2K9hjQScsoNJ0H0CUAY345YTnTm)
### Architecture (28 layers)
- ![https://remnote-user-data.s3.amazonaws.com/o3OaPIaP3PcG8ielCRpzgSjJVjh_xEIogqgIdRTKIc7w6LZsjFSTKvOnLQMkfVxxy6kQj0Vv_b7aELzuTbOQ8bzyzEs-ijhR3KCY6o5Wx7g4LAIcVZ3iPh-S_vhhJLSv](https://remnote-user-data.s3.amazonaws.com/o3OaPIaP3PcG8ielCRpzgSjJVjh_xEIogqgIdRTKIc7w6LZsjFSTKvOnLQMkfVxxy6kQj0Vv_b7aELzuTbOQ8bzyzEs-ijhR3KCY6o5Wx7g4LAIcVZ3iPh-S_vhhJLSv)  
- **GEMM**: General matrix multiply function. Often convs are implemented by a GEMM but require an initial reordering in memory called im2col to map it to a [[GEMM]]. But $ 1\times 1 $ does not require this reordering.
- Width Multiplier: Thinner Models
    - Define a parameter $ \alpha $ called multiplier. So the no. of input and output channels become $ \alpha M $ and $ \alpha N $.
    - $ \alpha \in (0,1] $ with typical settings of $ 1, 0.75, 0.5 $ and $ 0.25 $.
    - Reduce the number of parameters quadratically by roughly $ \alpha^2 $.
- Resolution Multiplier: Reduced Representation
    - Define a parameter $ \rho $ for input image and internal represetnation of every layer.
    - Implicitly set $ \rho$ by setting the input resolution.
    - Computation cost reduces to:
        - $$ D_K \cdot D_K \cdot \alpha M \cdot \rho D_F \cdot \rho D_F + \alpha M \cdot \alpha N \cdot \rho D_F \cdot \rho D_F $$ where $ \rho \in (0,1] $ (set implicitly so the input resolution is $ 224, 192, 160 $ or $ 128 $.
