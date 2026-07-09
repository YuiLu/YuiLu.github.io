---
title: GAMES101个人笔记（6）-材质与外观
tags: 
    - GAMES101
    - Notes
description: 图片与公式施工中~
mathjax: true
cover: 'https://cdn.jsdelivr.net/gh/YuiLu/Image_host@main/GAMES101/  (3).png'
abbrlink: 53257
date: 2024-01-05 16:00:00
top_img:
---

之前我们为了描述单位受照面吸收能量后辐射出去的Radiance分布情况，引入了BRDF函数，这个函数表示了材质如何与光线作用

而之后我们研究物体的材质和外观，就是在研究这些函数

# 漫反射材质

![漫反射材质](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E6%BC%AB%E5%8F%8D%E5%B0%84%E6%9D%90%E8%B4%A8.png)

在Blinn-Phong模型中，讨论漫反射系数的时候，我们只是经验性的引入$\frac{I}{r^2}$来表示到达着色点的能量
$$
L_d=k_d(\frac{I}{r^2})max(0,n·l)
$$
在学完渲染方程后，我们知道这其实并不准确，现在用$f_r$来准确计算这个漫反射系数

假设任意方向的入射光和出射光的Radiance和Irradiance都相等，着色点不吸收任何能量，且自发光项为0

则依渲染方程，可推出$f_r$如下
$$
L_o=\int_{\Omega^+} L_i \cdot f_r \cdot cos\theta_i\, \mathrm{d}\omega_i
=L_i \cdot f_r\int_{\Omega^+} cos\theta_i \, \mathrm{d}\omega_i\\

\int_{\Omega^+} cos\theta_i\, \mathrm{d}\omega_i
=\int_{\Omega^+} cos\theta_i \ sin\theta_i \, \mathrm{d}\theta_i \, \mathrm{d}\phi_i
=\int_0^{2\pi}\int_0^{\frac{\pi}{2}}sin\theta_i \, \mathrm{d}\sin\theta_i \ \, \mathrm{d}\phi_i= \pi\\

L_o=f_rL_i\pi\Longrightarrow f_r=\frac{L_o}{L_i \pi}=\frac{1}{\pi}\\
$$
定义一个反射率（albedo）$\rho\in[0,1]$与$f_r$相乘，于是通过$f_r$就可以控制材质的颜色变化
$$
f_r=\frac{\rho}{\pi}\in[0,\frac{1}{\pi}]
$$

# 光泽材质

光泽材质是介于漫反射材质与理想镜面反射材质之间的一种材质，光线的反射方向集中在一个小范围内

生活中的光泽材质有如打磨过的铜镜或者其他的一些金属材质

![光泽材质](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%85%89%E6%B3%BD%E6%9D%90%E8%B4%A8.png)

# 理想反射/折射材质

![理想反射折射材质](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E7%90%86%E6%83%B3%E5%8F%8D%E5%B0%84%E6%8A%98%E5%B0%84%E6%9D%90%E8%B4%A8.png)

光线到达材质表面被吸收一部分，同时发生镜面反射和镜面折射，这种材质被称为Ideal reflective / refractive material

## （完美）镜面反射

![完美镜面反射](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%AE%8C%E7%BE%8E%E9%95%9C%E9%9D%A2%E5%8F%8D%E5%B0%84.png)

公式分为两部分，左图（正视图）观察入射角和出射角，右图（俯视图）观察方位角

写出正确的完美镜面反射BRDF方程需要用到δ函数，在此从略

δ函数：https://wuli.wiki/online/Delta.html#note2

## 镜面折射

光从一种透明介质斜射入另一种透明介质时，由于光在两种介质中传播速度不同而使传播方向发生偏转的现象称为折射（初中物理）

生活中的折射现象有如：

三棱镜色散（不同波长的色光有不同的折射率）（依然用几何光学描述，不涉及波粒二象性等内容）

海水焦散，Caustics（不合适的翻译，主要还是由折射后聚焦引发，与散射关系不大）

# 斯涅耳定律

![斯涅耳定律](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E6%96%AF%E6%B6%85%E8%80%B3%E5%AE%9A%E5%BE%8B.png)

入射材质折射率 × 入射角正弦 = 出射材质折射率 × 折射角正弦

由图右侧常见折射率，钻石折射率较大，这就意味着光线通过钻石发生的偏转幅度比较大，这也是为什么钻石闪闪发光的原因

进一步推导

![折射定律](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E6%8A%98%E5%B0%84%E5%AE%9A%E5%BE%8B.png)

我们发现，折射的发生条件是入射材质的折射率小于出射材质折射率，一旦大于，就会发生全反射现象

![斯涅耳窗](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E6%96%AF%E6%B6%85%E8%80%B3%E7%AA%97.png)

人在水底只能看到锥形视野范围内的光，也是因为折射，相关现象被称为斯涅耳窗（snell's window）

## 双向散射分布函数（BSDF）

描述反射的分布函数被称为双向反射分布函数（BRDF），那么描述折射也需要一种分布函数

这种分布函数被称为双向折射(透射)分布函数（BTDF）

BRDF和BTDF统称为双向散射分布函数（BSDF）
$$
f_s=f_r+f_t
$$

## 菲涅尔项

观察下图中视角与反射结果的关系

![菲涅尔反射例子](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E8%8F%B2%E6%B6%85%E5%B0%94%E5%8F%8D%E5%B0%84%E4%BE%8B%E5%AD%90.png)

我们很容易发现，当我们用几乎垂直的视角看下去，基本看不到什么反射，而当我们的视角几乎水平时，反射结果特别明显

这是因为光线以不同角度入射会有不同的反射率，也就是所谓的菲涅尔效应

生活中的菲涅尔效应还有例如：

正对着窗子看能看清窗外景色，侧着看窗外看到大多室内的反射

站在湖边，透过近处的湖水能看见水底的情况，而望向远处只能看到群山的倒影

......

另外，在相同的入射角情况下，不同的材质也具有不同的反射率，即具有不同的菲涅尔项

下图即为两种不同的材质对应的菲涅尔项数据

|                     折射率为1.5的绝缘体                      |                             导体                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![菲涅尔项1](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E8%8F%B2%E6%B6%85%E5%B0%94%E9%A1%B91.png) | ![菲涅尔项2](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E8%8F%B2%E6%B6%85%E5%B0%94%E9%A1%B92.png) |

图中另外两条虚线表示光的极化性质，即光只沿一个方向振动情况下的菲涅尔项，现在的渲染器很少考虑这种情况

由图对应到现实一目了然，生活中各种金属的反射率一直都很高，所以我们习惯用镀银的玻璃作为镜子而不是用玻璃...

为了计算菲涅尔项，有非常复杂的公式，通过极化的菲涅尔数据做平均得到结果

但我们也有简单的近似（施利克近似 Schlick’s approximation），如图

![计算菲涅尔项](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E8%AE%A1%E7%AE%97%E8%8F%B2%E6%B6%85%E5%B0%94%E9%A1%B9.png)

这种近似方法认为菲涅尔曲线就是一条从  0°入射角菲涅尔项到90°入射角  的单调增函数，90°时$R_0=1$

推荐阅读：[光的反射与折射——从Snell、Fresnel到Schlick - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/303168568)

# 微表面模型

从理论上来说，地球表面是凹凸不平的，具有沙漠山丘等复杂地形，但在非常远的距离下拍摄，如下图所示的卫星图，我们却看到了如同在光滑球面上一样的高光

![卫星图](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%8D%AB%E6%98%9F%E5%9B%BE.png)

由此我们提出微表面模型，假设离得足够远的时候，微观表面可以被忽略，而最后看到一个宏观的结果

用微表面理论解释漫反射，即从微观看漫反射表面，每个微元表面都是完美镜面反射，都有各自的法线（微观上看是几何）

我们可以通过研究这些法线的分布来描述物体表面的粗糙程度

![微表面法线分布](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%BE%AE%E8%A1%A8%E9%9D%A2%E6%B3%95%E7%BA%BF%E5%88%86%E5%B8%83.png)

镜面反射的法线方向分布比较集中，而漫反射表面的法线分布比较分散

有了微表面模型，我们就可以提出在微表面下的更精确的BRDF方程

![微表面模型BRDF](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%BE%AE%E8%A1%A8%E9%9D%A2%E6%A8%A1%E5%9E%8BBRDF.png)

如图，F为菲涅尔项；D为法线分布，查询半程向量是否在法线分布内；G为几何项，由于在微表面上，对于那些几乎和表面平行的入射光，很容易发生互相遮挡的现象，从而使得部分微表面失去作用，我们把这种光线角度称为掠射角度（Grazing Angle），在这种角度下的着色会非常亮，G项就起到了一定的修正作用
$$
NDF_{GGTR}(n, h, \alpha) = \frac{\alpha^2}{\pi((n \cdot h)^2 (\alpha^2 - 1) + 1)^2}\\
G_{SchlickGGX}(n, v, k) = \frac{n \cdot v} {(n \cdot v)(1 - k) + k },\ (k_{direct} = \frac{(\alpha + 1)^2}{8},\ k_{IBL} = \frac{\alpha^2}{2})\\
G(n, v, l, k) = G_{sub}(n, v, k) G_{sub}(n, l, k)\\
F_{Schlick}(h, v, F_0) = F_0 + (1 - F_0) ( 1 - (h \cdot v))^5 \\
L_o(p,\omega_o) = \int\limits_{\Omega} (k_d\frac{c}{\pi} + \frac{DFG}{4(\omega_o \cdot n)(\omega_i \cdot n)}) L_i(p,\omega_i) n \cdot \omega_i \mathrm{d}\omega_i
$$

| ![微表面 (2)](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%BE%AE%E8%A1%A8%E9%9D%A2%20(2).png) | ![微表面 (3)](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%BE%AE%E8%A1%A8%E9%9D%A2%20(3).png) | ![微表面 (1)](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%BE%AE%E8%A1%A8%E9%9D%A2%20(1).png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |

微表面模型可以得到非常真实的渲染结果，因为他本身就是基于物理的渲染（PBR/PBS）

当然，微表面也有他的缺点，有时因为diffuse的太少，需要手动往上加点参数调节

# 各向同性/各向异性材质

各向同性（IsotropicMaterials）：微表面不存在方向性
各向异性（Anisotropic Materials）：微表面存在方向性

![各向同性各向异性](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%90%84%E5%90%91%E5%90%8C%E6%80%A7%E5%90%84%E5%90%91%E5%BC%82%E6%80%A7.png)

对于BRDF来说，这里所说的方向性就是指，如果入射光和出射光做一定方位角的旋转前后，BRDF方程不变，那么这种材质就是各向同性的，反之则为各向异性

![各向异性](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%90%84%E5%90%91%E5%BC%82%E6%80%A7.png)

再看几个各向异性的例子

|                            不锈钢                            |                             尼龙                             |                            天鹅绒                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![各向异性例1](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%90%84%E5%90%91%E5%BC%82%E6%80%A7%E4%BE%8B1.png) | ![各向异性例2](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%90%84%E5%90%91%E5%BC%82%E6%80%A7%E4%BE%8B2.png) | ![各向异性例3](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E5%90%84%E5%90%91%E5%BC%82%E6%80%A7%E4%BE%8B3.png) |

# BRDF性质总结

* 非负性：描述能量分布
* 线性性：可以被拆分成不同项的线性组合（ambient，diffuse，specular）

![BRDF非负性线性性](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/BRDF%E9%9D%9E%E8%B4%9F%E6%80%A7%E7%BA%BF%E6%80%A7%E6%80%A7.png)

* 可逆性：调换入射出射方向，BRDF渲染结果严格不变
* 能量守恒：出射光线的能量永远不能超过入射光线的能量

![BRDF可逆性能量守恒](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/BRDF%E5%8F%AF%E9%80%86%E6%80%A7%E8%83%BD%E9%87%8F%E5%AE%88%E6%81%92.png)

* 各向同/异性：如果是各项同性材质，则BRDF值只和相对方位角有关，四维的BRDF材质可以被降维为三维，并且根据可逆性，结果不需要考虑方位角的正负

![BRDF各项同性](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/BRDF%E5%90%84%E9%A1%B9%E5%90%8C%E6%80%A7.png)

# BRDF的测量

![理论or实际](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E7%90%86%E8%AE%BAor%E5%AE%9E%E9%99%85.png)

如图，推算出来的菲涅尔项和实际测量出来的往往会有很大差距，跟不用说BRDF了

如果工业上能直接测量材质的BRDF，就不需要如此复杂的理论推导而能直接使用数据了

测量BRDF的大致过程如下图所示

![测量BRDF大致原理](F:/-STUDY-/college/%E9%97%AB%E4%BB%A4%E7%90%AA_%E5%9B%BE%E5%BD%A2%E5%AD%A6%E5%85%A5%E9%97%A8/101/%E5%9B%BE%E7%89%87/p17-%E6%9D%90%E8%B4%A8%E4%B8%8E%E8%89%B2%E5%BD%A9/%E6%B5%8B%E9%87%8FBRDF%E5%A4%A7%E8%87%B4%E5%8E%9F%E7%90%86.png)

给定一个着色点，通过改变入射和出射的角度（改变光源与相机位置）进行测量

```
foreach outgoing direction wo
	move light to illuminate surface with a thin beam from wo
	for each incoming direction wi
		move sensor to be at direction wi from surface
		measure incident radiance
```

如算法伪代码所示，这样测出来的BRDF是四维的，这样的测量是非常费时的

为了提高效率，我们可以尽量让材质呈各向同性

就像之前说的，这不仅可以让BRDF从四维降至三维，还能由光路可逆性再砍去一半的测量

最后，关于BRDF的储存，有一个著名的库 ` MERL BRDF Database`，是三菱电子实验室和MIT合作的项目，不做细说