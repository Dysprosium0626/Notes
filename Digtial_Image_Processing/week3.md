### Image enhancement

#### Histogram operation

Intensity Transformation & Spatial Filtering

e.g.

$ s=r\\
s=clog(r+1)\\
s=f(r)\\
s=L-r(反转)\\
s=Cr^{\gamma}(显示器伽马校正)
$

#### Histogram Equalization

分布 -> 均匀分布

分布 $P_s(s)=P_r(r)|\displaystyle\frac{\partial r}{\partial s}|$

映射 $S=T(r)=(L-1)\displaystyle \int_{0}^{r}P_r(\omega)d\omega$

$\displaystyle\frac{ds}{dr}=\displaystyle\frac{dT(r)}{dr}=\frac{(L-1)\displaystyle \int_{0}^{r}P_r(\omega)d\omega}{dr}=(L-1)P_r(r)$代入

$P_s(s)=P_r(r)|\displaystyle\frac{\partial r}{\partial s}|=P_r(r)|\displaystyle\frac{1}{(L-1)P_r(r)}|=\displaystyle \frac{1}{L-1}$

需要取整

![](image/2021-08-01-14-14-18.png)

不一定是严格单调递增的但一定是单调递增的

#### Histogram Matching


两次Histogram Equalization


#### Local neighborhood operation
局部平均处理
模糊
