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

RGB -> YCbCr
Y:亮度通道
CbCr:色彩通道
$$\begin{bmatrix}
    Y\\
    Cb\\
    Cr\\
\end{bmatrix}=
\begin{bmatrix}
 & & &\\
 & & &\\
 & & &\\
\end{bmatrix}_{3\times 3}\cdot 
\begin{bmatrix}
    R\\G\\B
\end{bmatrix}$$

对每一个通道分别编码

### DCT(Discrete Cosine Transform)

#### why?
Mean Square Error MSE

$MES = \frac{1}{Number\ of\ pixels} \displaystyle \sum_{pixels}(\widetilde f - f)^2$

RMSE(root mean square error)

$RMES = [\frac{1}{Number\ of\ pixels} \displaystyle \sum_{pixels}(\widetilde f - f)^2]^\frac{1}{2}$

一个可逆的变换把原来的8x8变换成误差比较小的8x8

可用的：卡洛南-洛伊变换 Karhunen-Loeve Transform KLT
消除图像之间的相关性，把很多信息放在第一个元素，和其他元素是独立的

problem：image dependent实用性不强

DCT
image->$f(x,y)$

$$T(u, v)_{n\times n} = \displaystyle \sum_{x=0}^{n-1} \displaystyle \sum_{y=0}^{n-1} f(x, y)\ r(x, y, u, v)
$$
Inverse formula
$$
f(x,y) = \displaystyle \sum_{u=0}^{n-1} \displaystyle \sum_{v=0}^{n-1} T(u,v)\ s(x, y, u, v)
$$

$$r(x, y, u,v)=s(x, y,u,v)=\alpha(u)\alpha(v)cos[\frac{(2x+1)u\pi}{2n}]cos[\frac{(2y+1)v\pi}{2n}]$$

傅里叶变换的实部？

归一化：normalization

$$\alpha(u)=\begin{cases}
    \sqrt{\frac{1}{n}},u=0\\
    \sqrt{\frac{2}{n}},u \neq0
\end{cases}$$

r,s:基函数
将nxn的矩阵分解成基函数的线性组合

#### why DCT？
1. KLT需要DCT，一阶马尔可夫图像源，对某些图像DCT等于KLT
2. 对周期性的假设是不同的，不是以8为周期，一个像素点和与其相邻的像素点是相似的，符合认知

#### why 8x8?
compromise
1.节省空间
2.马尔科夫链条件可能可以成立，小范围假设中可以成立，但是大图像基本不可能成立，这个时候DCT=KLT

### Quantization

均匀量化

Max-Lloyd Optimal Quantizer


### JPEG_LS and MPEG

Predictive lossless compression
根据之前的像素值推测后面的像素值

**predictor**



### Run-length coding 游程编码

处理二值图像