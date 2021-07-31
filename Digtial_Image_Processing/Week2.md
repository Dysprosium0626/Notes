# Compression

### why？

冗余

compression standard:
JPEG/JPEG-LS(lossless)/JPEG-2000

image -> mapper(映射变换) -> quantizer -> symbol coder -> symbol decoder -> Inverse mapper


e.g.(quantizer)
$[\frac{17}{2}] \times 2$ 取整再乘

![](image/2021-07-31-13-42-37.png)
forward transform: DCT
symbol encoder: huffman coding

inverse transform:DCT

### Huffman coding
symbol encoder
**Lena**

Are all pixels/symbols equal?

Histogram（直方图）:每一个灰度值出现的次数

如果不压缩，每一个像素 8bits

how much compression

huffman coding

概率越大，编码越短

![](image/2021-07-31-13-58-24.png)

prefix free无前缀编码

$Entropy = H = -\displaystyle \sum_{symbols} p(s)\ log_{2}\ p(s)$

$p(s)$: probability
$log_2 p(s)$: length

**香农第一定理**
霍夫曼编码能得到的最短长度


### JPEG's 8 by 8 blocks

