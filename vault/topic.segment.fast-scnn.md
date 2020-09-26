---
id: a48ec74e-d671-449a-b386-cae358dedcdb
title: Fast scnn
desc: ''
updated: 1601113893794
created: 1601113893794
stub: false
---
# Fast scnn

## Meta Data:
- #citekey: poudelFastSCNNFastSemantic2019
- [[Poudel, Rudra P. K.]] #authors
- [[2019] #issued
- #title: Fast-SCNN: Fast Semantic Segmentation Network
- #publisher [[BMVC]]
- #topic: [[topic.segment]], [[Encoder-decoder]], #Efficient, [[DSConv]]
## **Abstract**
  - 'Learning to downsample' module to compute low-level features for multi-resolution branches.
  - Combines spatial detail at high resolution with deep features extracted at lower resolutioin.
## **Methods for speed and memory:**
  - **Network Quantization**: Floating point multiplications are costly compared to integer or binary operations, so quantization methods for DCNN filters and activation values can improve runtime.
  - **Network Compression**: Pruning is applied to reduce pre-trained network size.
  - **Factorization of Convolution**: [[topic.segmentation.mobilenet]] decomposes standard convolution into depthwise convolution and a $ 1\times 1 $ pointwise convolution ([[DSConv]]).
  - Efficient Redesign of DCNNs.
- ![https://remnote-user-data.s3.amazonaws.com/n_BAl21OhbAvdz6SYeYWa39UiB1pMYzUX7HQ-CRHwhRNXmqkrX-qAOMDF4V5f4Yyh7U6fyVadJ80HXQiRi8vHuPSDTFaZoNgvMgWCUB5c1H58uQcyaBHvKZ-qgg5o_AA](https://remnote-user-data.s3.amazonaws.com/n_BAl21OhbAvdz6SYeYWa39UiB1pMYzUX7HQ-CRHwhRNXmqkrX-qAOMDF4V5f4Yyh7U6fyVadJ80HXQiRi8vHuPSDTFaZoNgvMgWCUB5c1H58uQcyaBHvKZ-qgg5o_AA)
## 1. Learn to Downsample
  - Employ three layers to ensure low-level feature sharing is valid.
      - first layer Conv2D
      - remaining two layers are [[DSConv]].
      - All layers to downsample module use stride 2, followed by [[Batch Normalization]] and [[ReLU]]. The spatial kernel size is $ 3\times 3$
      - $ $Omit nonlinearity between depthwise and pointwise convolutinos
  - DSConv:: Depth-wise separable Convolutional layers.
## 2. Global Feature Extractor
  - takes the output of the learning to downsample module ($ 1/8 $ resolution of the original input).
  - ![https://remnote-user-data.s3.amazonaws.com/-bG0uR-VwY58sRJ3N18tS3WckjpLElBSUNKlwRjRqcAtlpT-RlT0XSTPqvs2X5doub6oN8SYFIMtc_xJMYQYBBbHM2ayn-Pjsvo4TQpN_ppN7y73rtbrmMCRD4-NGPQ1](https://remnote-user-data.s3.amazonaws.com/-bG0uR-VwY58sRJ3N18tS3WckjpLElBSUNKlwRjRqcAtlpT-RlT0XSTPqvs2X5doub6oN8SYFIMtc_xJMYQYBBbHM2ayn-Pjsvo4TQpN_ppN7y73rtbrmMCRD4-NGPQ1)  
  
## 3. Feature Fusion Module
## 4. Classifier
