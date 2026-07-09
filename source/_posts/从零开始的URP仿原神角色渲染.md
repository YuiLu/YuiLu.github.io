---
title: 从零开始的URP仿原神角色渲染
tags:
  - Blogs
  - 卡通渲染
description: 早期学习卡通渲染的一些记录（图片施工中）
mathjax: true
top_img: '/images/topimg/{04C1544E-4D28-47b3-941B-2F7767E3BD07}.png'
cover: /images/cover/result.png
abbrlink: 44076
date: 2024-01-17 16:00:00
---
# 前言
从去年到现在学习TA已经大概有半年多了，最近也开始逐渐意识到要去做一些自己的实践，于是经过一个礼拜左右时间的研究学习，通过这样一个仿原神渲染的尝试，对之前卡渲的一些理论做了一下初步的实现。
不得不说，“只有实践才能出真知”这句话真的太对了，之前看RTR之类资料的时候觉得这块不过如此，而只有到真正自己上手的时候才明白自己还有太多的东西浮于表面一知半解，包括哪些地方需要什么样的trick，哪里如何优化才能让代码的效率更高，还有最重要的自己定位bug解决bug的能力（别的不说，这甚至还是我第一次buildin转URP....）
套用之前看到的图就是这样：
![C7DC53DDC05F7F8DF94122B40AAFE510.jpg](https://cdn.nlark.com/yuque/0/2022/jpeg/23115229/1651839535848-39172531-673e-41d9-b2ef-b03df653ec18.jpeg#averageHue=%23f9f9f7&clientId=ua34e33ef-0961-4&errorMessage=unknown%20error&from=paste&height=321&id=u0cfe0f80&originHeight=519&originWidth=640&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35183&status=error&style=none&taskId=u8a3b84cb-bd4c-413e-b902-c6cdeda017f&title=&width=396)
我这辈子都搞不懂了...
所以就算整体做下来代码量就三四百行，这一个礼拜的学习对我自己而言收获还是挺大的，因此希望通过写这样一篇文章能对我自己的学习过程做一个记录。文章可能不会事无巨细面面俱到，过于拾人牙慧的东西我就直接把链接逐一贴出略过了，而相对的我会留下更多空间去记录自己的思考过程和踩坑经历（如果有哪里理解不到位的话，还请大佬在评论区指正补充）
[从零开始的卡通渲染](https://www.zhihu.com/column/c_1215952152252121088)
[原神角色渲染Shader分析还原](https://zhuanlan.zhihu.com/p/360229590)
[【Unity技术美术】 原神Shader渲染还原解析](https://zhuanlan.zhihu.com/p/435005339)
[从仿原神角色渲染到MMD制作(小记)](https://zhuanlan.zhihu.com/p/490406107)
[从零开始的原神角色渲染](https://zhuanlan.zhihu.com/p/468209534)
那么话不多说让我们开始吧！
# 风格分析
## 一些概念
**PBR、NPR与三渲二**
在喵刀老师去年JTRP教程的[20:19](https://www.bilibili.com/video/BV1AA411A7RR?)处有详细说明，以下进行概括
> 卡通渲染属于非真实感渲染（Non-photorealistic rendering，简称NPR）。对应的还有真实感渲染(Photorealistic rendering)。后者旨在渲染真实感的画面，而前者则追求更加有艺术感的画面效果，例如手绘风格的画面

我们常说的PBR（Physically-based rendering）是一种以现实为参考的渲染方法，而NPR则是与PBR相对的概念，强调风格化，包括但不限于油画，铅笔画，水墨画等不同类型。三渲二属于NPR的一个子集，特指一些用3D手段还原2D赛璐璐风格的技法
三渲二的画面特点通常包含以下几点：

- 阴影简单而主观
- 颜色信息单一，以大色块和硬边过渡为主
- 主要通过笔触感很强的勾线来凸显形状
- 特殊的脸部线条画法
- 条状高光，与光方向无关的边缘光
- 背光处理（能够大幅提升画面质感）
- ......

![P5KC{UFS3F8QO%E]_3IUAFV.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651846151394-bf7eb62e-ab2b-4ddd-b450-66a3b0df95be.png#averageHue=%23a2a798&clientId=ua34e33ef-0961-4&errorMessage=unknown%20error&from=paste&height=541&id=ud1094521&originHeight=676&originWidth=1205&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1005285&status=error&style=none&taskId=ucaf19f42-801f-4883-a17c-5d991962fee&title=&width=964)
不同风格的三渲二作品
**赛璐璐，平涂与厚涂**
赛璐璐和厚涂的区别：
赛璐璐：特指一种颜色界限层次分明的上色风格，色块大，图层多，边缘锐利，大量出现在日本动画制作中，属于一种极端的平涂
厚涂：运用笔刷和技巧堆砌颜色，技术要求高，画面通常表现出立体感强、色彩丰富、质感厚实的特点
## 原神的角色渲染
原神的角色渲染还是有一部分继承了三蹦子的技术的，可以参考[官方古早的视频](https://www.youtube.com/watch?v=egHSE0dpWRw&t) 12:14-28:01 部分
由于能力有限，本次的还原并未涉及游戏内shader的截帧分析，所以说并不是真正意义上的还原，只是在基础的卡通渲染上加了一些自己的想法付诸实现
![image.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651923548730-ddf02e16-237c-465d-b0c0-9b70e5509546.png#averageHue=%23fbfafa&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=558&id=u8cc66437&originHeight=698&originWidth=1087&originalType=binary&ratio=1&rotation=0&showTitle=false&size=41672&status=error&style=none&taskId=uc8bdea3c-916d-4ce0-9fbb-2c93cb22595&title=&width=869.6)
目前实现的效果：
![2022.05.07阶段性成果GIF.gif](https://cdn.nlark.com/yuque/0/2022/gif/23115229/1651921855335-17266abb-c68f-47d1-a4cc-5cb69209973d.gif#averageHue=%2395a5bc&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=384&id=ufa511760&originHeight=480&originWidth=856&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1425130&status=error&style=none&taskId=u759d9717-1fd2-4f13-a721-21e13401db0&title=&width=684.8)
肉眼可见的一堆问题......不过也只能这样了，期末周精力实在达不到，后续有更改会在这继续更新
# 贴图分析
首先还是来看一下我们手上有哪些资源：
![B3`ITXZ%VD[UHSX(SJ_SV%E.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651318026520-15c16f36-39b8-4a63-ad12-ee6c3b568ea2.png#averageHue=%23e6dfdb&clientId=u7629753c-7c10-4&errorMessage=unknown%20error&from=paste&height=344&id=u14700a1c&originHeight=430&originWidth=746&originalType=binary&ratio=1&rotation=0&showTitle=false&size=128738&status=error&style=none&taskId=uea7e28db-b597-4b63-8cd4-e08c19a3784&title=&width=596.8)
除了三张Diffuse是官方配布，其他均需要自行获取
Body和Hair分别有一张LightMap（ILM），观察可知其四个通道分别为：
R：高光范围
![Y2N]F)$3E2]XCMCB[[XF8UR.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651479545647-d4f2c8ad-8f22-49a3-8ca9-b32ee408c738.png#averageHue=%2392918e&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=390&id=u4476adf6&originHeight=488&originWidth=1400&originalType=binary&ratio=1&rotation=0&showTitle=false&size=204119&status=error&style=none&taskId=ud0cca84b-35fb-4760-b9e7-d09a0147abe&title=&width=1120)
g：AO Mask（黑色-固定阴影，灰色-动态阴影，白色-完全亮部）
![Z_`CW~J]2OV0L9W7O3XMN)K.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651479550305-7f5c3258-e017-45b6-a210-d1ad69a7a7e9.png#averageHue=%2371706e&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=390&id=uf0c2bd44&originHeight=487&originWidth=1400&originalType=binary&ratio=1&rotation=0&showTitle=false&size=242700&status=error&style=none&taskId=u8108bb07-f415-477f-8ba2-b092c0c7269&title=&width=1120)
b：高光强度
![%IZF}8KPNW$P@`M19U)W}CS.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651479554404-c54d26d2-6763-4faa-926e-fc397c434d3f.png#averageHue=%2373716f&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=390&id=uc105c6a8&originHeight=488&originWidth=1400&originalType=binary&ratio=1&rotation=0&showTitle=false&size=207626&status=error&style=none&taskId=u69821579-129d-4a24-9326-95d986ae6fd&title=&width=1120)
a：Ramp阈值
![`S[)1911T$~[%L_F2_IJRKN.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651479558991-51b1bafb-2b62-4651-914a-503a43517149.png#averageHue=%2373716e&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=390&id=u1405a4d5&originHeight=488&originWidth=1397&originalType=binary&ratio=1&rotation=0&showTitle=false&size=184386&status=error&style=none&taskId=u196b5529-2088-462c-934d-83cb7970079&title=&width=1117.6)
身体和头发分别对应两张Ramp图，每张ramp都分了冷色调和暖色调的渐变条带，有点像UE的Curve Atlas
![K2}FGB3QNM~%52~TCHO8F5W.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651319433368-28678456-7f62-4400-8b4a-f6c123931092.png#averageHue=%23444342&clientId=u7629753c-7c10-4&errorMessage=unknown%20error&from=paste&height=822&id=u656bc558&originHeight=1027&originWidth=1917&originalType=binary&ratio=1&rotation=0&showTitle=false&size=156316&status=error&style=none&taskId=uab1301bd-4d2c-4ee9-ad2f-b3247bce2bc&title=&width=1533.6)
![B`E$YE@LDE]R]%XG)VZB$3N.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651319516359-1b6c8bd5-ac3a-4d1b-b58b-64f6b8d94fb3.png#averageHue=%23464544&clientId=u7629753c-7c10-4&errorMessage=unknown%20error&from=paste&height=822&id=u3d07533b&originHeight=1028&originWidth=1916&originalType=binary&ratio=1&rotation=0&showTitle=false&size=155059&status=error&style=none&taskId=u300fe855-a98b-4372-b0c3-164e0c398a3&title=&width=1532.8)
不同角色的ramp的排列方式和条带数量都是有区别的，比如甘雨这套，body一共5种渐变色，hair有4种，而对于排列方式则大概分为两种，一种是256*16，暖8冷8（大概率有3像素以上的留白），另一种是20像素的，暖5*2 冷5*2，所以需要根据不同类型选择不同的采样方式，这个后面还会详细说到（或者可以直接使用曲线进行手动调色，自由度更高）
两种不同的ramp：

| ![Z5F%3HMBS73GAKH28H_DOYL.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651399873348-5740d8b7-28ea-4577-8c16-75a32fd2d7af.png#averageHue=%23edc5ba&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=295&id=u626720d9&originHeight=504&originWidth=348&originalType=binary&ratio=1&rotation=0&showTitle=false&size=4801&status=error&style=none&taskId=ua571be27-aecf-404e-8b18-022ee87aceb&title=&width=203.39999389648438) | ![UT)O]9L3}LD%G$)BU2DDZA5.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651399871157-1da1e910-e5e6-42c6-92ef-d538a70c965c.png#averageHue=%23726c79&clientId=u161fa7aa-7488-4&errorMessage=unknown%20error&from=paste&height=293&id=u29510ad8&originHeight=408&originWidth=283&originalType=binary&ratio=1&rotation=0&showTitle=false&size=3687&status=error&style=none&taskId=u87a85abc-3a31-4d9c-8f8b-72cf11c461f&title=&width=203.40000915527344) |
| --- | --- |

剩下还有两张，一张脸部SDF还有一张MetalMap，在做脸部阴影和身体身体金属部件高光的时候都会起到特殊的作用，也是等到后面提到了再说吧
关于贴图设置，除了Diffuse图和Ramp图，其他全部取消勾选sRGB，法线图（如果有的话）纹理类型选择Normal Map，SDF纹理压缩设置为None（UE改成灰阶），不然会有很难看的锯齿
![RM`B1{(Y0J51REWIN@R`@@A.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1665816267313-38100aaa-cbf3-44d2-b455-86e6356b82aa.png#averageHue=%23393737&clientId=u8171bcba-2b22-4&errorMessage=unknown%20error&from=paste&height=410&id=u8ec54953&originHeight=456&originWidth=360&originalType=binary&ratio=1&rotation=0&showTitle=false&size=67817&status=error&style=none&taskId=ua54cd393-5b7f-49d6-ab66-7b705fd2638&title=&width=324)![(6O{`_13IR61NCSLR~8854A.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1665816310467-2520ae9f-0b8f-40fc-929f-89e1c494b19a.png#averageHue=%23272626&clientId=u8171bcba-2b22-4&errorMessage=unknown%20error&from=paste&height=410&id=u7a5fd35b&originHeight=558&originWidth=472&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36726&status=error&style=none&taskId=u8d1fd4fa-5f9f-4658-bee4-1ec45c74819&title=&width=347)


# 描边
那么现在就让我们开始正式的代码编写。
首先来看描边。描边通常是卡通角色渲染中拿到模型后第一件需要处理的事情，一方面是因为它极其基础，另一方面也是因为它有可能会影响后续其他效果的调整（如边缘光的粗细），这里虽然采用的还是传统的背面法线外扩的方式，但是我有对其中几个经典的问题进行了改进，如下：

- 描边粗细随摄像机远近发生变化
- 硬表面描边断裂
- 视口比例修正

第一个问题是因为，我们一般的法线外扩都是在视口空间完成的，最终渲染到屏幕之前，硬件底层还会帮我们做一步透视除法（即除w将坐标映射到$[-1,1]$的NDC空间），要想保持描边粗细不变，我们就必须在外扩距离的基础上乘上w来消除它的影响
第二个问题也老生常谈了，问题出在模型本身的法线都是垂直于当三角网格所在平面的，一个顶点可能会依据邻接的三角面选择多个法线方向，而法线外扩通常在顶点着色器就完成了全部的处理，那么这时候就需要我们提前对模型进行法线上的合并。详细的做法可以参考喵刀老师的文章：
[【Job/Toon Shading Workflow】自动生成硬表面模型Outline Normal](https://zhuanlan.zhihu.com/p/107664564)
有几个小点需要注意的是，文中提到的 JOBS 是引擎基于ECS的一套多线程管理系统，需要提前在Package Manager中进行环境的配置，这里建议直接向manifest.json文件中添加"com.unity.collections": "0.17.0-preview.18"，以安装相关插件，因为entity在直接安装的过程中很有可能发生版本不兼容等各种问题，我在这上面折腾了好久，最后还是google找到了适合自己的解决方案......
喵刀老师的这个方法的话，是通过在模型导入的时候直接生成一个副本然后做模型后处理实现的，相比2173大佬的那个将平滑法线写入模型切线的编辑器工具，这个可以在引擎关闭时仍保留平滑法线的数据，方便了很多（当然也可以直接在dcc里写工具，只要能解决问题就行）
如果用的是喵刀老师的方法，需要注意一下顶点色通道的问题，因为官方给的模型的g通道原来用来控制Ramp偏移的，所以要避免这个问题，要么就用第二套顶点色，要么后面再自己开个参数手动控制偏移，不论哪种方法都造不成什么大问题
平滑法线输出如图，绿色代表左上，黄色代表右上，黑色左下，红色右下：
![C8`[`2K`@Z3OJTRAFKASM5E.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651323197568-a1ea7dba-bbce-4d39-9747-5cccc51c447d.png#averageHue=%233f6eb5&clientId=u7c9f8c6b-ad1f-4&errorMessage=unknown%20error&from=paste&height=313&id=z9O3Q&originHeight=391&originWidth=849&originalType=binary&ratio=1&rotation=0&showTitle=false&size=81770&status=error&style=none&taskId=u3869abc3-074f-4136-b08f-b9f90e88dcc&title=&width=679.2)
最后一个问题，视口比例修正，这个就很简单了，直接拿参数算一下乘上去就好
片元着色器部分代码如下：
```glsl
// 获取预先烘焙进顶点色的切线空间平滑法线，修复描边断裂，同时避免蒙皮动画可能发生的错误描边
// UnpackNormalmapRGorAG会自动将RG变为AG，也就将顶点色控制描边粗细变化一并实现了
half3 smoothNormal = normalize(UnpackNormalmapRGorAG(v.color));
// 将法线从切线空间变换到世界空间
float3x3 tangentTransform = float3x3(o.worldTangent, o.worldBiTangent, o.worldNormal);
half3 worldOutlineNormal = normalize(mul(smoothNormal, tangentTransform));
// 再从世界空间变换到裁剪空间，此处 * pos.w 是为了消除齐次除法的影响，使得在摄像机远近发生变化时，描边粗细保持不变
half3 outlineNormal = TransformWorldToHClip(worldOutlineNormal) * pos.w;
// 求得屏幕宽高比，修正描边以适配窗口
float aspect = _ScreenParams.x / _ScreenParams.y;
pos.xy += 0.001 * _OutlineWidth * v.color.a * outlineNormal.xy * aspect * _EnableOutline;
o.pos = pos;
```
效果：
![M9TBJWGQ2[Q5R47ZTCLE[H1.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651978398152-7c4ed2e8-d11b-410c-9179-626329d268d6.png#averageHue=%237b7b7a&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=421&id=u16667bd3&originHeight=834&originWidth=753&originalType=binary&ratio=1&rotation=0&showTitle=false&size=173569&status=error&style=none&taskId=u82cf9603-85f7-4c1b-8aab-276af66a698&title=&width=380.3999938964844)
不处理
![2YB$3YCNXNO$KMB`{FN~26O.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651929637268-d5106fd2-3dc5-475a-8ecd-e5f21dd53b06.png#averageHue=%237d7d7d&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=413&id=u24f47a4e&originHeight=1198&originWidth=1115&originalType=binary&ratio=1&rotation=0&showTitle=false&size=300940&status=error&style=none&taskId=uf654991f-6f9a-4570-b098-c0743aaee7c&title=&width=384)
模型后处理
![%A5I[(@V6[8}Q_4$7](`3KG.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651978474518-7ba1429f-9594-4567-8973-74733ba6dcd9.png#averageHue=%237d7d7d&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=431&id=u46d1b954&originHeight=865&originWidth=812&originalType=binary&ratio=1&rotation=0&showTitle=false&size=196162&status=error&style=none&taskId=u6b0d38af-3ef5-48a3-915c-c94881d26a4&title=&width=404.6000061035156)
存进切线
可以看到平滑后还是有点效果的（再想把质量往上提的话就直接用p+吧hhh）
2021.05.08：
今天早上爬起来看了眼JTRP的Readme，里面中说平滑法线的这个流程已经失效了，但我2021.3.1f1c1 collection0.17.0-preview.18这个版本还可以用，应该就是包版本的问题
# Ramp
接下来轮到漫反射
在常规的卡通渲染当中，一般都会通过冷暖色调分离、阴影边缘硬化等手段来使画面达到风格化的目的，而原神这种用ilm贴图配合ramp实现色调控制的方法，也是早在好几年前《GUILTY GEAR Xrd》就已经存在的思路。值得一提的是，三蹦子的ramp和原神这套虽然原理差不多，但有些地方还是有一定差别的（虽然不管怎么样最后都会有一定trick,,,）
![](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651930115093-1246103f-0d0c-46c0-afb5-525f99f85602.png#averageHue=%237a756d&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&id=u4dfc96ee&originHeight=217&originWidth=800&originalType=url&ratio=1&rotation=0&showTitle=false&status=error&style=none&taskId=u6db61e8b-8641-4a8f-86c5-03b065a4d01&title=)
这里我就主要说一下甘雨的ramp图采样思路吧（不适用其他角色）
![GKX2HTD8~IN3EB6$N5ICVSX.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651480682206-a0971767-97c6-4c54-9296-0ce38b0d4c44.png#averageHue=%23185328&clientId=udf4b8113-e78b-4&errorMessage=unknown%20error&from=paste&height=472&id=ubc1bf4ee&originHeight=590&originWidth=1147&originalType=binary&ratio=1&rotation=0&showTitle=false&size=44172&status=error&style=none&taskId=u88364dfb-142d-414a-9b44-14e6719e84e&title=&width=917.6)
经过上面的贴图分析我们知道，我们采样的像素分为冷暖两种色调，以适应白天和夜晚不同的光线环境（实际上游戏里还有不同天气等诸多别的影响，不知道是用额外的ramp还是后处理实现的），那么我们要做的就是通过shader_feature来进行采样的切换。具体的采样方法上面这张图已经表示的非常清楚了，为了尽可能的采样到像素中间，以避免颜色的混杂，必须对采样方式实行精确的控制。这里有一点比较迷惑的是，甘雨LightMap的a通道看上去只分了三层，但是ramp却给了五个色带，多出来的那几个色带没看懂是用来干嘛的，所以我最后直接让lightmap自己选去了（将0-1灰度映射到1-5代入等差数列...），最后看起来也没什么太大的问题....
对于头发部分，因为头发部分只有4个色带，所以映射关系就是0-1到1-4，然后根据ps中观察到的渐变形态，主观的采样了第一和第三条，也不一定是正确答案
有了RampY，剩下的就简单了，RampX根据原来的lambert值，做smoothstep重映射，只保留0到一定数值的渐变，而大于这一数值的全部采样ramp最右边的颜色，这样一来就既可以保留阴影色的过渡，又可以形成硬边，将明暗很好的区分开来
[Shader实验室: smoothstep函数](https://zhuanlan.zhihu.com/p/157758600)
[GeoGebra Classic - GeoGebra](https://www.geogebra.org/classic/sw9mtpdd)
最后乘上AO和基础色，Ramp部分就基本完成了
ramp图第一行
代码：
```glsl
half4 ToonPassFrag(v2f i) : SV_TARGET
{
    float4 BaseColor = SAMPLE_TEXTURE2D(_MainTex, sampler_MainTex, i.uv) * _MainColor;
    float4 LightMapColor = SAMPLE_TEXTURE2D(_LightMap, sampler_LightMap, i.uv);
    Light mainLight = GetMainLight();
    half4 LightColor = half4(mainLight.color, 1.0);
    half3 lightDir = normalize(mainLight.direction);
    half3 viewDir = normalize(_WorldSpaceCameraPos - i.worldPos);
    half3 halfDir = normalize(viewDir + lightDir);

    half halfLambert = dot(lightDir, i.worldNormal) * 0.5 + 0.5;
  
    // Base Ramp
    // 依据原来的lambert值，保留0到一定数值的smooth渐变，大于这一数值的全部采样ramp最右边的颜色，从而形成硬边
    halfLambert = smoothstep(0.0, _ShadowSmooth, halfLambert);
    // 常暗阴影
    float ShadowAO = smoothstep(0.1, LightMapColor.g, 0.7);

    float RampPixelX = 0.00390625;  //0.00390625 = 1/256
    float RampPixelY = 0.03125;     //0.03125 = 1/16/2   尽量采样到ramp条带的正中间，以避免精度误差
    float RampX, RampY;
    // 对X做一步Clamp，防止采样到边界
    RampX = clamp(halfLambert*ShadowAO, RampPixelX, 1-RampPixelX);

    // 灰度0.0-0.2  硬Ramp
    // 灰度0.2-0.4  软Ramp
    // 灰度0.4-0.6  金属层
    // 灰度0.6-0.8  布料层，主要为silk类
    // 灰度0.8-1.0  皮肤/头发层
    // 白天采样上半，晚上采样下半

    //— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —
    // Base Ramp
    if (_IsNight == 0.0)
        RampY = RampPixelY * (33 - 2 * (LightMapColor.a * 4 + 1));
    else
        RampY = RampPixelY * (17 - 2 * (LightMapColor.a * 4 + 1));

    float2 RampUV = float2(RampX, RampY);
    float4 rampColor = SAMPLE_TEXTURE2D(_RampMap, sampler_RampMap, RampUV);
    half4 FinalRamp = lerp(rampColor * BaseColor * _ShadowColor, BaseColor, step(_RampShadowRange, halfLambert * ShadowAO));

    //— — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — — —
    // Hair Ramp
    #if _SHADERENUM_HAIR
        if (_IsNight == 0.0)
            RampY = RampPixelY * (33 - 2 * lerp(1, 3, step(0.5, LightMapColor.a)));
        else
            RampY = RampPixelY * (17 - 2 * lerp(1, 3, step(0.5, LightMapColor.a)));
        RampUV = float2(RampX, RampY);
        rampColor = SAMPLE_TEXTURE2D(_RampMap, sampler_RampMap, RampUV);
        FinalRamp = lerp(rampColor * BaseColor * _ShadowColor, BaseColor, step(_RampShadowRange, halfLambert * ShadowAO));
    #endif
    return FinalRamp;
}
```
效果：
![ZI398D)TP5PM$62[L%0O$Y5.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651941704059-c5b9d628-9546-4565-929a-ac9256f98fc0.png#averageHue=%23827d75&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=431&id=ub864a92a&originHeight=1186&originWidth=1094&originalType=binary&ratio=1&rotation=0&showTitle=false&size=639886&status=error&style=none&taskId=ue435b9e1-c006-429e-867d-ba70a989ae0&title=&width=398)
# SDF脸部阴影
SDF这一块其实没啥好说的，相关的学习资料有很多，实现的过程也非常简单（虽然我被各种向量点乘绕了好久hhh）大概的原理是用一张黑白高度图作为阴影阈值，与Front向量和Light向量的点积做比较，从而精确地控制光线在不同角度下脸部的阴影形状。采用这种方法，可以很好的代替原先修正面部法线的复杂流程，轻松达到平滑面部阴影过渡的效果
![image.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651987091496-58b9a171-9c02-40a4-ab8d-cdcce967bca6.png#averageHue=%2378806e&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=244&id=udbc09483&originHeight=612&originWidth=796&originalType=url&ratio=1&rotation=0&showTitle=false&size=501190&status=error&style=none&taskId=udb7df1b5-254f-43ed-bd30-477955a5e3c&title=&width=318)![H8{J97U1(C`PMHV]N$Q2{3B.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651987115690-7d1f8129-d298-4fec-9630-86e5a085bbb8.png#averageHue=%23494852&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=361&id=u8fa26799&originHeight=451&originWidth=300&originalType=binary&ratio=1&rotation=0&showTitle=false&size=116751&status=error&style=none&taskId=u50759dd5-e8e6-4c45-bf00-9917b974afd&title=&width=240)
   伦勃朗光
![K)WFF8Y@}6IE{)C2QH8H{W7.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651976175303-456ffa3e-9325-495b-81ca-c38962587212.png#averageHue=%238a97c4&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=154&id=u851f4f84&originHeight=192&originWidth=222&originalType=binary&ratio=1&rotation=0&showTitle=false&size=80309&status=error&style=none&taskId=ufcd4b50e-b0ce-418a-b2ef-ad82e8f1128&title=&width=177.6)             ![image.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651986423484-b8969508-6808-4843-a1de-e39ec32854bc.png#averageHue=%23b9a5d5&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=153&id=ub020cd91&originHeight=408&originWidth=434&originalType=binary&ratio=1&rotation=0&showTitle=false&size=249483&status=error&style=none&taskId=u64935fbf-4937-4c53-9fa1-80b7e9e16c5&title=&width=163.1999969482422)
不用之前                                                  用了之后
立竿见影！
## 资产生成
因为学校数字图像处理课期末大作业的缘故，我对这方面进行了比较详细的研究。一共分为两种方法，一种靠SDF程序化生成，另一种直接在csp或ps用等高线画。其中后者不会在此详细说明，详情可以参考如下教程
[【教程】使用csp等高线填充工具制作三渲二面部阴影贴图_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV16y4y1x7J1?)
这里就简单配合几张图说下SDF做这张贴图怎么做
### 8ssedt
有关什么是SDF可以去看看GAMES202 p5，或者直接看我笔记上实时阴影的部分，简单来说，它就是通过一个场定义出了平面或空间中每个点距其最近物体的最短距离，其中，S虽然翻译过来是有向（signed），但实际上它是一个标量场，只不过通过正负号标识出了物体的内外而已
[GAMES202高质量实时渲染-个人笔记：实时阴影](https://zhuanlan.zhihu.com/p/464408139)
在这里，SDF的主要应用体现在几何形变上
关于SDF图的生成有一种交8ssedt的算法，主要用到了动态规划的思想
[Signed Distance Field](https://zhuanlan.zhihu.com/p/337944099)
可运行程序：
[如何快速生成混合卡通光照图](https://zhuanlan.zhihu.com/p/356185096)
整个过程分成了两个grid来做，每个grid有2个pass，一趟做下来会进八次循环......
我配合着做了几张动图，可能会比较好理解一点：
![pass1_gif.gif](https://cdn.nlark.com/yuque/0/2022/gif/23115229/1651982961735-a28193ec-9f6a-4f8a-b6f5-7e57e55ba2fa.gif#averageHue=%23e3e2e2&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=804&id=u73f09072&originHeight=1005&originWidth=977&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1197566&status=error&style=none&taskId=u706ea2f2-a7a6-4473-bfcb-72734202e31&title=&width=781.6)
第二个Pass大差不差：
![pass2_gif.gif](https://cdn.nlark.com/yuque/0/2022/gif/23115229/1651989081551-cc28d698-8029-44fb-9bdd-949fb06c9a2e.gif#averageHue=%23e3e0e0&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=804&id=u7031a37a&originHeight=1005&originWidth=977&originalType=binary&ratio=1&rotation=0&showTitle=false&size=403144&status=error&style=none&taskId=u6ab32609-6e3e-4cda-a2b2-e6d8bd4b4bc&title=&width=781.6)
算法优化：
[记一次代码优化(C++)](https://www.jianshu.com/p/58271568781d)
### 二值图融合
到这里，有些人可能还不是很清楚我们要干嘛。其实我们最终的目的很简单，就是将下面这几张二值图融合起来，而融合的参照，或者说插值所要用到的权重，就是我们上面生成的SDF
![image.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651985366801-4798909a-16fb-40fe-88a8-920738265dfd.png#averageHue=%23a4a3a3&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&id=u6056f2ce&originHeight=168&originWidth=1090&originalType=url&ratio=1&rotation=0&showTitle=false&size=26217&status=error&style=none&taskId=u03e07cb1-00ac-42c8-9615-b022403e943&title=)
![blend.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651989678888-7d41bb27-2539-4043-8c6c-838a3c4bb181.png#averageHue=%232e2323&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=509&id=u02b4da07&originHeight=636&originWidth=748&originalType=binary&ratio=1&rotation=0&showTitle=false&size=102251&status=error&style=none&taskId=ufd184701-ace7-409e-9dd0-89dafe7753d&title=&width=598.4)
试图解释...
还是直接上代码吧：
```cpp
float scale = 1.f / (images.size() - 1);
for (int step = 0, i = images.size() - 1; i >= 1; --i, ++step)
{
    for (int y = 0; y < imageHeight; ++y)
    {
        for (int x = 0; x < imageWidth; ++x)
        {
            // lerp
            int sdf_index = y * imageWidth + x;
            int pixel_index = sdf_index * imageChannel;
            
            int left_border_index = i;
            int right_border_index = i - 1;
            
            float sdf1 = images[left_border_index]->sdf[sdf_index] / 255.f;
            float sdf2 = images[right_border_index]->sdf[sdf_index] / 255.f;
            sdf1 = 2.f * sdf1 - 1.f;
            sdf2 = 2.f * sdf2 - 1.f;
            
            float left = step * scale;
            float right = (step + 1) * scale;
            
            if (sdf1 * sdf2 > 0)
            {
                if (right_border_index == 0)
                {
                    if (sdf1 < 0)
                    {
                        for (int c = 0; c < imageChannel; ++c)
                            image[pixel_index + c] = 255;
                    }
                }
                else
                {
                    // nothing
                }
            }
            else
            {
                // sdf1 < 0 , sdf2 > 0
                float totalDis = abs(sdf1) + abs(sdf2);
                float t = abs(sdf2) / totalDis;
                t = 1 - t;
                for (int c = 0; c < imageChannel; ++c)
                {
                    float dst = left * (1 - t) + (right * t);
                    // dst = std::pow(dst, 1 / 2.2f); // gamma for linear display
                    image[pixel_index + c] = dst * 255;
                }
            }
        }
    }
}

```
看不懂可以去看下面这篇的后半部分
[图形学基础|基于SDF的卡通阴影图_桑来93的博客-CSDN博客_sdf图](https://blog.csdn.net/qjh5606/article/details/119958786)
## 使用贴图
最后终于到怎么使用阴影图了，老样子我还是把我参考的文章放在前面
[神作面部阴影渲染还原](https://zhuanlan.zhihu.com/p/279334552)
核心代码就一行：
```cpp
return lerp(BaseColor, ShadowColor, step(FaceMap.r, 1-FdotL));
```
一开始当 FdotL=0 时，脸上开始出现被照亮的区域，随着F和L的夹角减小，FdotL增大，1-FdotL减小，脸上越来越多的区域被判断为亮面，直到 FdotL=1 完全受光
在这之后，灯光向量通过RdotL=0的临界点，贴图UV进行一次翻转，以完全相反的过程重复一遍采样，即1-FdotL增大，阴影面积相应增加
伪代码如下：
```cpp
if (RdotL < 0)
	FaceMap = FaceMap;
else
	FaceMap = FaceMapInverse;

if (FaceMap.r > 1-FdotL)
    return BaseColor;
else
    return ShadowColor;
```
画了一张图描述这个过程，长下面这样：
![V%FB%610S$])5KSHM~WVQ4P.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651990428473-0f1604ee-cf57-4f8d-a3c5-08daa0fa8761.png#averageHue=%23eae9e9&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=394&id=ua26cb363&originHeight=492&originWidth=1182&originalType=binary&ratio=1&rotation=0&showTitle=false&size=55257&status=error&style=none&taskId=ub1dd3717-663d-42dd-897f-a9bf7526616&title=&width=945.6)
到这一步，我们的效果就基本已经完成了，下面强调几个注意点
第一，贴图翻转是对UV进行水平翻转，不能在采样结果上做1-x运算，即：
```cpp
float FaceMap = lerp(LightMapColor.r, 1-LightMapColor.r, step(0, RdotL)) * step(0, FdotL);
```
第二，出现头发阴影与脸部阴影对不上的问题的时候，不能直接在采样数据上±Offset，会导致阴影跳变，解决方案是像雪羽大佬那样，构建一个旋转矩阵对灯管向量进行偏移
```cpp
float sinx = sin(_FaceShadowOffset);
float cosx = cos(_FaceShadowOffset);
float2x2 rotationOffset1 = float2x2(cosx, sinx, -sinx, cosx); //顺时针偏移
float2x2 rotationOffset2 = float2x2(cosx, -sinx, sinx, cosx); //逆时针偏移
float2 FaceLightDir = lerp(mul(rotationOffset1, lightDir.xz), mul(rotationOffset2, lightDir.xz), step(0, RdotL));
```
第三，编写完代码之后通常会发现阴影会出现很难看的锯齿，这时候需要回到编辑器将贴图mipmap关掉，并将其类型设置为shadowmask
![Z~%6V2}%MYHR{WV]1M88NJH.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651994895584-4d2b7677-87d5-44fa-8db5-0c0f727c3f71.png#averageHue=%234f4c4b&clientId=u357d18e8-45ea-4&errorMessage=unknown%20error&from=paste&height=821&id=u86b28548&originHeight=1026&originWidth=1921&originalType=binary&ratio=1&rotation=0&showTitle=false&size=838342&status=error&style=none&taskId=u397a7a63-4808-40b9-98db-88e9f591333&title=&width=1536.8)
大功告成！（完整代码在文章末尾）
# 高光
高光这里大量借鉴了清清的做法（链接在上面），分成了step高光，blinn-phong和matcap金属高光，不过目前好像在最后混合的时候出了点问题，以后有机会修一修吧（必须修！）
头发的高光也没特别细调，只是把blinn-phong和metal全关了稍微调了调裁边视角光，后面打算把各向异性也加上，期末周了真的顾不上......
代码（没什么借鉴意义）：
```glsl
// 高光
half4 BlinnPhongSpecular;
half4 MetalSpecular;
half4 StepSpecular;
half4 FinalSpecular;
// ILM的R通道，灰色为裁边视角高光
half StepMask = step(0.2, LightMapColor.r) - step(0.8, LightMapColor.r);
StepSpecular = step(1 - _StepSpecularGloss, saturate(dot(i.worldNormal, viewDir))) * _StepSpecularIntensity * StepMask;
// ILM的R通道，白色为 Blinn-Phong + 金属高光
half MetalMask = step(0.9, LightMapColor.r);
// Blinn-Phong
BlinnPhongSpecular = pow(max(0, dot(i.worldNormal, halfDir)), _BlinnPhongSpecularGloss) * _BlinnPhongSpecularIntensity * MetalMask;
// 金属高光
float2 MetalMapUV = mul((float3x3) UNITY_MATRIX_V, i.worldNormal).xy * 0.5 + 0.5;
float MetalMap = SAMPLE_TEXTURE2D(_MetalMap, sampler_MetalMap, MetalMapUV).r;
MetalMap = step(_MetalSpecularGloss, MetalMap);
MetalSpecular = MetalMap * _MetalSpecularIntensity * MetalMask;
                
FinalSpecular = StepSpecular + BlinnPhongSpecular + MetalSpecular;
FinalSpecular = lerp(0, BaseColor * FinalSpecular * _SpecularColor, LightMapColor.b) ;
FinalSpecular *= halfLambert * ShadowAO * _EnableSpecular;
```
效果：
![I5`S)JPI%`74U[M$J5I1`SB.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651942798102-7e676721-91dd-4fdc-ace7-276e24029f92.png#averageHue=%23817d75&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=337&id=u6f53203a&originHeight=819&originWidth=857&originalType=binary&ratio=1&rotation=0&showTitle=false&size=426443&status=error&style=none&taskId=u424e449b-19d2-426c-9fc9-c43ef50661f&title=&width=352.6000061035156)
![OF4G]%7__70EWC%Z4GFVVAC.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651942862523-38ec19a2-9cac-44d7-a766-e7f7c0261b91.png#averageHue=%23a0c5d1&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=280&id=udb83753a&originHeight=421&originWidth=559&originalType=binary&ratio=1&rotation=0&showTitle=false&size=316632&status=error&style=none&taskId=u9c6397b3-40a5-4e61-8e12-dcc1dbfeb84&title=&width=372)![DLWOSKR)VDW%{~}Z(A_N~6Q.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651942892590-d027cd81-6609-4575-872f-b44e798a520d.png#averageHue=%239fc6d2&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=250&id=ua20fab94&originHeight=478&originWidth=703&originalType=binary&ratio=1&rotation=0&showTitle=false&size=419152&status=error&style=none&taskId=ud911ff1b-cf73-4d2e-a109-13e35dab84b&title=&width=367.3999938964844)
左图是单独调整的效果（叠加会爆白），右图是结合basecol调整后单独显示的结果（基本等于没有...）
# 边缘光
再来看边缘光部分，现在主流的边缘光实现方式基本就两种，一种菲涅尔，一种屏幕空间等距边缘光，当然也可以两种都用，但据我观察，原神的边缘光并不具备随视角变化而变化的特性，加上反而感觉有些画蛇添足，所以我这里就没加
屏幕空间等距边缘光的实现原理的话，可以参考下面这两篇文章，大概思路就是在原先模型深度的基础上沿法线方向外扩一段距离，再拿它和原深度值比较，二者深度差大于某个阈值的时候即判定为边缘
[Unity URP Shader 与 HLSL 自学笔记六 等宽屏幕空间边缘光](https://zhuanlan.zhihu.com/p/365339160)
[【JTRP】屏幕空间深度边缘光 Screen Space Depth Rimlight](https://zhuanlan.zhihu.com/p/139290492)
有点像描边，但不用开新的pass，直接在片元做就完事了。我这里把之前用来做描边用的平滑法线复用了一下，虽然感觉没啥必要...代价就多了次矩阵运算，所以加不加就见仁见智吧
```glsl
//记得打开摄像机的深度纹理
TEXTURE2D(_CameraDepthTexture); SAMPLER(sampler_CameraDepthTexture);

...

// 屏幕空间深度等宽边缘光
// 屏幕空间UV
float2 RimScreenUV = float2(i.pos.x / _ScreenParams.x, i.pos.y / _ScreenParams.y);
// 法线外扩偏移UV，把worldNormal转换到NDC空间
float3 smoothNormal = normalize(UnpackNormalmapRGorAG(i.color));
float3x3 tangentTransform = float3x3(i.worldTangent, i.worldBiTangent, i.worldNormal);
float3 worldRimNormal = normalize(mul(smoothNormal, tangentTransform));
float2 RimOffsetUV = float2(mul((float3x3) UNITY_MATRIX_V, worldRimNormal).xy * _RimOffset * 0.01 / i.pos.w);
RimOffsetUV += RimScreenUV;
                
float ScreenDepth = SAMPLE_DEPTH_TEXTURE(_CameraDepthTexture, sampler_CameraDepthTexture, RimScreenUV);
float Linear01ScreenDepth = LinearEyeDepth(ScreenDepth, _ZBufferParams);
float OffsetDepth = SAMPLE_DEPTH_TEXTURE(_CameraDepthTexture, sampler_CameraDepthTexture, RimOffsetUV);
float Linear01OffsetDepth = LinearEyeDepth(OffsetDepth, _ZBufferParams);

float diff = Linear01OffsetDepth - Linear01ScreenDepth;
float rimMask = step(_RimThreshold * 0.1, diff);
// 边缘光颜色的a通道用来控制边缘光强弱
half4 RimColor = float4(rimMask * _RimColor.rgb * _RimColor.a, 1) * _EnableRim;

...

Pass
{
    Tags {"LightMode" = "DepthOnly"}
}
```
插句题外话，这里是将世界法线转到NDC，除以w没什么好说的，而《入门精要》p275 讲到有关深度和法线纹理的效果的时候，从NDC重建世界坐标也做了一次“透视除法”，虽然这个和这里边缘光没啥关系，但当时看这里对这个步骤困惑了很久，想了想还是放在这里一并记下吧
![FO~D]G9%]QA9T~46(KUODL5.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651674911792-958413b7-5374-45bf-8fe9-9f53cd81e8df.png#averageHue=%23f8f8f8&clientId=ua34e33ef-0961-4&errorMessage=unknown%20error&from=paste&height=393&id=u63fee7e8&originHeight=491&originWidth=573&originalType=binary&ratio=1&rotation=0&showTitle=false&size=54649&status=error&style=none&taskId=u64632915-1fbf-407f-8883-8e14df37fd1&title=&width=458.4)
效果：
![0%CRZY3XALS6}57S)P@[OXE.png](https://cdn.nlark.com/yuque/0/2022/png/23115229/1651945531979-45f52b43-4599-4e80-8cf0-3ad8351bfb4e.png#averageHue=%234c4c4b&clientId=u32c63bef-2a11-4&errorMessage=unknown%20error&from=paste&height=379&id=u270c7938&originHeight=474&originWidth=537&originalType=binary&ratio=1&rotation=0&showTitle=false&size=140985&status=error&style=none&taskId=u9076feac-152d-4a0f-a3d2-70c62a77115&title=&width=429.6)
prprpr
调整的过程中，需要注意边缘光是辅助元素，不能太过显眼，借用月神的话来说，就只要调到那种“不仔细看察觉不到”的程度即可（除非是风格需要）
# 总结 & Future Works
完整代码github链接：
[GitHub - YuiLu/GenshinCharacterShading: 通过编写一个仿原神渲染的shader，来学习URP和卡通渲染相关知识](https://github.com/YuiLu/GenshinCharacterShading)
除了某些显而易见的bug，还有很多个性化调整的点，比如shadow和shadowAO色调分离，Rim边缘软硬控制，body上第二层halfLambert等等等等，不胜枚举，目前计划是等暑假多学点东西之后，先把高光的问题修了（还有皮肤也有问题），在看着实现下头发的各向异性和眼睛的PBR...未来的工作还有很多，希望有一天能成为喵刀colin那样的大佬吧
