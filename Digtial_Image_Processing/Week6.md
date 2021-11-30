### Partial Differential Equations in Image Processing

经典的图像处理基于离散形式

Sum instead of integrals
Re-definition of classical continuous operators, such as gradients, Laplacian, etc

**the PDE approach**
连续域
图像是迭代的结果：PDEs
数值分析：如何实现连续域的数学工具

Accuracy
Formal analysis(形式分析)

#### Planar Differential Geometry
曲线上的平面理解

$C(p)=\{x(p), y(p)\}, p \in [0,1]$
闭合曲线

切线$\vec{t}=\frac{C_p}{|C_p|}=C_s$单位长度 微分方程 $C_p=\frac{\partial C}{\partial p}=[X_p, y_p]$
法线$C_{ss}=\kappa\vec{n}$ 二阶导数

曲率 Curvature 二阶导数的模

**Linear Transformations**
仿射变换 Affine $\{\widetilde{x}, \widetilde{y}\}^{T}= A\{x, y\}^T + \overline{b}$

欧几里得变换（旋转和平移） Euclidean $A=[\overline{u_1}, \overline{u_2}]， where<\overline{u_1}, \overline{u_2}>=0，<\overline{u_i}, \overline{u_ii}>=1$正交矩阵，内积为0，单位向量

仿射运动 Equi-Affine $\{\widetilde{x}, \widetilde{y}\}^{T}= A\{x, y\}^T + \overline{b}, det(A)=1$ 行列式为1

Euclidean invariant signature $\{s, \kappa(s)\}$

欧几里得变换 曲率不变（一阶导数和二阶导数都不变）

![](image/2021-08-04-17-05-04.png)

Cartan Theorem

欧几里得变换

只做平移和旋转，函数是不会变的

微风不变性

仿射变换？

$I_2(x,y)=I_1(T_1(x,y), T_2(x,y))$

$\begin{pmatrix}
    T_1(x,y)\\
    T_2(x,y)
\end{pmatrix}=
\begin{pmatrix}
     a&b\\
    c&d
\end{pmatrix}
\begin{pmatrix}
   x\\y
\end{pmatrix}+
\begin{pmatrix}
    e\\f
\end{pmatrix}$

Equi-Affine: $det\begin{pmatrix}
     a&b\\
     c&d
\end{pmatrix}=1$

参数化：$C(p), C(r)$不同的参数得到的曲线是一样的 invariant
$w = \displaystyle \int F(C,C_p,C_pp,\cdots)dp= \displaystyle \int F(C,C_r,C_rr,\cdots)dr$

**Euclidean arclength**

Length

$ds=\sqrt{dx^2+dy^2}=\frac{dp}{dp}\sqrt{dx^2+dy^2}=dp\sqrt{{\frac{dx}{dp}}^2+{\frac{dy}{dp}}^2}=|C_p|dp$
$s = \displaystyle\int |C_p|dp\\
|C_s|=1$
$Length L= \displaystyle \int_0^1|C_p|dp=\displaystyle \int_0^1<C_p, C_p>^{1/2}dp=\displaystyle\int _0^L ds$

**Equi-Affine arclength**

Area

$(C_v, C_{vv})=1\; 二阶矩阵\\
v=\displaystyle \int (C_p, C_pp)^(1/3)dp\\
v=\displaystyle \int (C_s, C_{ss})^(1/3)ds=\displaystyle \int \kappa^{1/3}ds\\
dv=\kappa^{1/3}ds$

曲率
利用$(C_v, C_{vv})=1$两边同时对v求导
$\frac{d}{dv}(C_v, C_{vv})=0\\
(C_v, C_{vv})+(C_v, C_{vvv})=0\\
(C_v, C_{vvv})v=0$
$C_v //C_{vvv}\\
C_{vvv}=\mu C_v$
$\mu$是仿射曲率

#### Surface Differential Geometry

$S(n,v)=\{x(u,v),y(u,v),z(u,v)\}$

Normal $\vec{N}=\displaystyle \frac{S_u \times S_v}{|S_u \times S_v|}$

Area element $dA=|S_u \times S_v|$

Total area $A=\displaystyle \iint |S_u \times S_v|dudv$

![](image/2021-08-04-18-00-01.png)

参数表达式
$S:\mathbb{R}^2 \rightarrow \mathbb{R}^3 $

$S(u,v)=\{x=u, y=v, z(u,v)\}$

![](image/2021-08-04-18-05-34.png)

Normal Curvature
$\kappa_n=<C_{ss}, \vec{N}>$

Principle Curvatures
$\kappa_1=max_\theta(\kappa)$
$\kappa_2=min_\theta(\kappa)$

Mean Curvature $H=\displaystyle\frac{\kappa_1+\kappa_2}{2}$
Gaussian Curvature $K=\kappa_1\kappa_2$

#### Curve Evolution

Following

切线方向上的运动不会影响曲线的形状
曲线进化是法线方向上的变化

**Curvature flow曲率运动**

$C_t=C_{ss}=\kappa \vec{n}$

![](image/2021-08-05-14-59-55.png)

欧氏空间中的变化曲率不变
![](image/2021-08-05-15-03-12.png)

heat flow,最终会变成一个圆


**Affine heat equation**

$C_t =C_{vv}= \kappa^{1/3}\vec{n}$

仿射不变

最终会变成一个椭圆（和圆一样，经过仿射变换可以变成圆）

**Constant flow**
$C_t =\vec{n}$
创建和曲线平行等距的曲线

无数个半径相同的圆的包络线
类似惠更斯原理
![](image/2021-08-05-15-09-21.png)

可以改变曲线的拓扑结构(法线变换)

![](image/2021-08-05-15-11-06.png)

反应扩散方程

![](image/2021-08-05-15-16-39.png)

$
Length L_t=-\displaystyle \int_0^L\kappa Vds\\
Area A_t=\displaystyle \int_0^L Vds\\
Curvature \kappa_t=V_{ss}+\kappa^2V
$

e.g.

$ V=1 \quad Constant\ flow\\
L_t=-\displaystyle \int_0^L\kappa Vds=-\displaystyle \int_0^L\kappa ds=-2\pi\\
A_t=\displaystyle \int_0^L Vds=\displaystyle \int_0^L ds=-L\\
\kappa_t=V_{ss}+\kappa^2V=\kappa^2$

The curve vanishes at$t=\displaystyle \frac{L(0)}{2\pi}$

Riccati equation $\kappa(p,t)=\displaystyle\frac{\kappa(p,0)}{1-t\kappa(p,0)}$

Singularity at(shock)$t=\rho(p,0)$



$ V=\kappa \quad Curvature\ flow\\
L_t=-\displaystyle \int_0^L\kappa Vds=-\displaystyle \int_0^L\kappa^2 ds\\
A_t=\displaystyle \int_0^L Vds=\displaystyle \int_0^L \kappa ds=-2\pi\\
\kappa_t=V_{ss}+\kappa^2V=\kappa_{ss}+\kappa^3$

The curve vanishes at$t=\displaystyle \frac{A(0)}{2\pi}$

![](image/2021-08-05-15-28-35.png)

Geodesic active contours

$C_t=(g(x,y)\kappa-<\nabla g(x,y),\vec{n}>)\vec{n}$

不要收缩在一个点，要收缩在图形的边界上，停留在梯度高的地方


#### Level Sets and Curve Evolution

曲线：平面上所有使得特定方程等于0的点
$C=\{(x,y)|\phi(x,y)=0\}$ 零水平集

The level set normal
 $\vec{N}=-\displaystyle\frac{\nabla \phi}{|\nabla \phi|}\quad (\vec{T}=\displaystyle\frac{\nabla \phi}{|\nabla \phi|})$

The level set curvature
$\kappa = div(\displaystyle\frac{\nabla \phi}{|\nabla \phi|})$
$div(\alpha, \beta)=\alpha_x+\beta_y$

如何使函数变形，让他停留在我们想要的边界上
$\phi(x,y):\mathbb{R^2}\rightarrow\mathbb{R}$
$C=\{(x,y)|\phi(x,y)=0\}$ 

![](image/2021-08-05-16-02-54.png)

网格上操作，离散化，不需要理会拓扑结构

#### Calculus of Variation

变分法

扩展求函数极值的方法，泛函functional的极值

$\displaystyle \int F(u,u_x)dx$

求u，使得函数取最小值的函数

只有当欧拉-拉格朗日方程$(\frac{\partial }{\partial u}-\frac{d}{dx}\frac{\partial }{\partial u_x})F(u,u_x)=0$成立

![](image/2021-08-08-14-33-14.png)

两点之间可以求出来是条直线方程

![](image/2021-08-08-14-39-57.png)

微分方程，梯度下降法
移植到泛函上：
![](image/2021-08-08-14-41-35.png)


#### Anisotropic Diffusion

各向异性扩散

各向同性不考虑是否有边界（高斯滤波、图像平均），各向异性沿着边界方向进行平均，是一种降噪/图像增强的过程

Heat equation$\displaystyle \frac{\partial I(x,y,t)}{\partial t}=\Delta I$

$\displaystyle \frac{\partial I(x,y,t)}{\partial t}=div(g(|\nabla I|))\nabla I$

引入函数，类似计数器

利用欧拉-拉格朗日方程$min_I \displaystyle \int_\Omega \rho(|\nabla I|)d\Omega \rightarrow \displaystyle\frac{\partial I(x,y,t)}{\partial t}=div(\rho'\displaystyle\frac{\nabla I}{|\nabla I|})$

total variation
全变分

#### Active contours

Edge detection:local information

![](image/2021-08-08-15-07-15.png)

