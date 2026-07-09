---
title: Personal Info
date: 2024-01-13 15:57:22
type: "about_cn"
top_img: /img/top_img_eva_compress.jpg
---
*.gif 已转为 webm 格式，加载速度大幅提升*
# About Me
* 本科就读于上海对外经贸大学，数据科学与大数据技术专业
* 于2021年9月开始技术美术相关技能的学习（渲染特效方向）至今已自主完成 GAMES101、GAMES202的学习，并在知乎和语雀以笔记形式记录了自己的学习过程
* 技术宅，具有较强的学习主动性，能快速吸收新知识并用于实际应用。喜欢研究特殊效果的实现原理
* 对自己的未来有着明确的规划，清楚自己的学习路线，并正有条不紊的落实中
* 爱好：指弹吉他<span class='heimu' title="你知道得太多了">（只听不弹）</span>/电吉他，ACGN爱好者，喜欢一切与计算机图形相关的技术
# Skills
* C++，Cg/HLSL，Python（基本掌握），C#（了解）
* 良好的数理统计基础，对深度学习有基本的了解，持续关注AIGC相关领域发展动向
* 具有一定计算机图形学相关的知识储备，了解基本的数据结构与算法原理
* 能够熟练使用UE4 Niagara进行特效制作
* 对Unity中的特效模块有所了解，并具有一定Shader编写经验（Build-in，URP）
* 对常见的卡通渲染手法有所了解，并在Unity尝试过效果的落地与实现
* 能够使用Blender进行简单模型的制作，并在未来有bpy，mel等脚本语言的学习规划
# Independent Works
## 护盾受击效果
<video autoplay loop muted playsinline poster="/images/folio/shield_hit.gif"><source src="/images/folio/shield_hit.webm" type="video/webm"></video>
WPO，蓝图受击响应逻辑
## 基于学习的特效智能LOD生成方案研究
<video autoplay loop muted playsinline poster="/images/folio/NiagaraAutoLod.gif"><source src="/images/folio/NiagaraAutoLod.webm" type="video/webm"></video>
项目由腾讯IEG引擎图形学远程课题实践活动发起。通过该项目初步对深度学习和强化学习相关概念进行了一定程度的学习和探索，了解到了特效制作过程中的一些性能评判标准，也借此尝试了部分理论的建模，并在此过程中从零到一学习了UE5插件开发的相关知识，最后成功实现了如图所示的Niagara批量添加LOD模块的功能（Slate编写等）
# Tutorial Works
## C++软光追渲染器
<!-- ![Alt text](../images/GAMES101_PathTracing.png) -->
![](/images/folio/GAMES101_PathTracing.png)
<!-- ![Alt text](../images/In_One_Weekend_spp=100_small.png) -->
![](/images/folio/In_One_Weekend_spp=100_small.png)
<!-- ![Alt text](../images/The_Next_Week_Final_spp=1024_small.png) -->
![](/images/folio/The_Next_Week_Final_spp=1024_small.png)
跟随 GAMES101 的课程进度，独立完成了BVH和蒙特卡洛微表面的实现，后通过 Peter Shirely 手写光追系列教程完成了整个渲染器的搭建，并在此基础上实现了 Tone Mapping 和多线程加速，未来还有计划加入更多诸如模型 IO、包围盒优化等技术点的实现
## III Elemental shrine
综合使用UE4 Niagara、材质与蓝图实现的一系列高级特效
### 陨石 & 火龙卷
<video autoplay loop muted playsinline poster="/images/folio/陨石_火龙卷.gif"><source src="/images/folio/陨石_火龙卷.webm" type="video/webm"></video>
视差陨石坑，后期模糊，技能联动，斜切UV...
### 落雷 & 电弧
<video autoplay loop muted playsinline poster="/images/folio/落雷.gif"><source src="/images/folio/落雷.webm" type="video/webm"></video>
<video autoplay loop muted playsinline poster="/images/folio/电弧.gif"><source src="/images/folio/电弧.webm" type="video/webm"></video>
Ribbon，直线场，伤害异步，Event拖尾...
### 冰锥 & 歼灭
<video autoplay loop muted playsinline poster="/images/folio/冰锥_歼灭.gif"><source src="/images/folio/冰锥_歼灭.webm" type="video/webm"></video>
视差冰面，SSS冰锥，复杂索敌逻辑，Spawn Group...
## Unity URP - 仿原神渲染
<video autoplay loop muted playsinline poster="/images/folio/甘雨仿原神渲染.gif"><source src="/images/folio/甘雨仿原神渲染.webm" type="video/webm"></video>
Ramp阴影过渡，屏幕空间等距边缘光，背面法线外扩描边，SDF面部阴影...
