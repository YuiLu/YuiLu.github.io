---
title: Personal Info
date: 2024-01-13 15:57:22
type: "about_cn"
top_img: /img/top_img_eva_compress.jpg
toc: true
---
<style>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}
@media (max-width: 1024px) {
  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (max-width: 640px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }
}
.skill-card {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 14px 16px;
  border: 1px solid rgba(128,128,128,0.15);
  border-radius: 8px;
  background: rgba(128,128,128,0.03);
}
[data-theme="dark"] .skill-card {
  border-color: rgba(255,255,255,0.08);
  background: rgba(255,255,255,0.02);
}
.skill-card .skill-icon {
  width: 24px;
  height: 24px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
#article-container .skill-card .skill-icon img {
  width: 24px;
  height: 24px;
  object-fit: contain;
  display: block;
  margin: 0;
}
.skill-card .skill-name {
  font-size: 0.9em;
  font-weight: 600;
  flex-shrink: 0;
  width: 72px;
  line-height: 24px;
  display: flex;
  align-items: center;
}
.skill-card .skill-track {
  flex: 1;
  min-width: 0;
  height: 8px;
  background: rgba(128,128,128,0.15);
  border-radius: 4px;
  overflow: hidden;
}
[data-theme="dark"] .skill-card .skill-track {
  background: rgba(255,255,255,0.08);
}
.skill-card .skill-fill {
  height: 100%;
  border-radius: 4px;
  background: linear-gradient(90deg, #59ADB8, #4a9aa4);
  transition: width 0.8s ease;
}
.skill-card .skill-icon svg {
  width: 24px;
  height: 24px;
  display: block;
}
.edu-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
@media (max-width: 640px) {
  .edu-grid {
    grid-template-columns: 1fr;
  }
}
.edu-card {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 20px;
  border: 1px solid rgba(128,128,128,0.15);
  border-radius: 8px;
  background: rgba(128,128,128,0.03);
}
[data-theme="dark"] .edu-card {
  border-color: rgba(255,255,255,0.08);
  background: rgba(255,255,255,0.02);
}
.edu-card .edu-badge {
  width: 56px;
  height: 56px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
#article-container .edu-card .edu-badge img {
  width: 56px;
  height: 56px;
  object-fit: contain;
  display: block;
  margin: 0;
}
.edu-card .edu-info {
  flex: 1;
  min-width: 0;
}
.edu-card .edu-name {
  font-size: 1em;
  font-weight: bold;
  color: #59ADB8;
}
[data-theme="dark"] .edu-card .edu-name {
  color: #7fd0d9;
}
.edu-card .edu-major {
  font-size: 0.9em;
  margin: 4px 0;
  opacity: 0.9;
}
.edu-card .edu-date {
  font-size: 0.85em;
  opacity: 0.7;
}
.work-entry {
  margin-bottom: 24px;
  padding-left: 16px;
  border-left: 2px solid #59ADB8;
}
.work-entry .work-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  flex-wrap: wrap;
}
.work-entry .work-company {
  font-size: 1.05em;
  font-weight: bold;
  color: #59ADB8;
}
[data-theme="dark"] .work-entry .work-company {
  color: #7fd0d9;
}
.work-entry .work-date {
  font-size: 0.85em;
  opacity: 0.7;
}
.work-entry .work-role {
  font-size: 0.9em;
  opacity: 0.75;
  margin: 2px 0 8px;
}
.work-entry .work-desc {
  font-size: 0.9em;
  line-height: 1.7;
}
.work-entry .work-desc ul {
  margin: 4px 0 0;
  padding-left: 18px;
}
.folio-video {
  max-width: 100%;
  border-radius: 8px;
  margin: 8px 0;
}
.lang-switch {
  display: inline-flex;
  gap: 2px;
  padding: 2px;
  border-radius: 999px;
  background: rgba(128,128,128,0.12);
  font-size: 0.75em;
  font-weight: 600;
  line-height: 1;
  vertical-align: middle;
}
#article-container .lang-switch a {
  padding: 4px 12px;
  border-radius: 999px;
  text-decoration: none;
  color: #666;
  transition: background 0.2s, color 0.2s;
}
[data-theme="dark"] #article-container .lang-switch a {
  color: #ccc;
}
#article-container .lang-switch a:hover {
  color: #59ADB8;
  text-decoration: none;
}
#article-container .lang-switch a.active {
  background: #59ADB8;
  color: #fff;
}
#article-container .lang-switch a.active:hover {
  color: #fff;
}
.about-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 10px;
}
.about-head h1 {
  margin: 0;
  border: none;
}
</style>

<div class="about-head">

# About Me

<div class="lang-switch">
  <a href="/about_cn/" class="active">简体中文</a>
  <a href="/about_en/">English</a>
</div>

</div>

* 于 2022 年开始系统接触游戏图形与 AI 交叉领域的相关技能（渲染/AI/特效/工具链）
* 以学生一作身份在 ECCV 2026 发表可控视频镜头预演生成系统相关成果
* 良好的英文读写能力（雅思7.0），能够无障碍阅读前沿英文文献与技术文档
* 良好的数理统计与数据科学基础，具备模型训练与数据集构建处理经验
* 具有一定计算机图形学相关的知识储备，了解基本的数据结构与算法原理
* 技术宅，具有较强的自驱力与学习主动性，能快速吸收新知识并用于实际应用。喜欢研究游戏内特殊效果的实现原理
* 熟悉常见的卡通渲染手法，分别在 Unity 和 UE5 尝试过效果的落地与实现
* 爱好：ACGN爱好者，Kigurumi、摄影，指弹吉他<span class='heimu' title="你知道得太多了">（只听不弹）</span>/电吉他，喜欢一切与计算机图形相关的技术

# Skills

<div class="skills-grid">
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" alt="C#"></span><span class="skill-name">C#</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" alt="HLSL"></span><span class="skill-name">Cg/HLSL</span><div class="skill-track"><div class="skill-fill" style="width:85%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python"></span><span class="skill-name">Python</span><div class="skill-track"><div class="skill-fill" style="width:75%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg" alt="C++"></span><span class="skill-name">C++</span><div class="skill-track"><div class="skill-fill" style="width:60%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/unrealengine/unrealengine-original.svg" alt="UE5"></span><span class="skill-name">UE5</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/unity/unity-original.svg" alt="Unity"></span><span class="skill-name">Unity</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/blender/blender-original.svg" alt="Blender"></span><span class="skill-name">Blender</span><div class="skill-track"><div class="skill-fill" style="width:55%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="#FF4713" xmlns="http://www.w3.org/2000/svg"><path d="M0 19.635V24h3.824A8.662 8.662 0 0 1 0 19.635zm16.042-4.555c0-4.037-3.253-7.92-8.111-8.089C4.483 6.873 1.801 8.136 0 10.005v4.209c1.224-3.549 4.595-5.158 7.419-5.128 3.531.041 6.251 2.703 6.275 5.72 0 2.878-1.183 4.992-4.436 5.516-1.774.296-4.548-.754-4.436-3.434.065-1.381 1.138-2.162 2.366-2.106-1.207 1.618.39 2.801 1.52 2.561a2.51 2.51 0 0 0 1.966-2.502c0-1.017-.958-2.662-3.333-2.6-2.936.068-4.785 2.183-4.85 4.797-.071 3.28 3.007 5.457 6.174 5.483 4.633.059 7.395-2.984 7.377-7.441zM0 0v6.906a12.855 12.855 0 0 1 7.931-2.609c6.801 0 11.134 4.762 11.131 10.765 0 4.17-1.946 7.308-4.995 8.938H24V0H0z"/></svg></span><span class="skill-name">Houdini</span><div class="skill-track"><div class="skill-fill" style="width:45%"></div></div></div>
</div>

# Work Experience

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">网易雷火事业群 · 伏羲人工智能实验室</span>
    <span class="work-date">2026.05 — 至今</span>
  </div>
  <div class="work-role">决策智能组 · 人工智能算法实习生</div>
  <div class="work-desc">
    <ul>
      <li>参与永劫无间AI Bot的研发，负责上层剧本挖掘，从录像中提炼可复用的战术模式</li>
      <li>基于时间知识图谱与聚类构建挖掘管线，由Agent查询图谱生成剧本对接对局投放</li>
    </ul>
  </div>
</div>

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">腾讯IEG · 互动娱乐事业群</span>
    <span class="work-date">2025.11 — 2026.05</span>
  </div>
  <div class="work-role">国内发行线 · 生态发展部 · 技术美术实习生</div>
  <div class="work-desc">
    <ul>
      <li><strong>独立负责UE5 AI智能打光系统的研发</strong>，从零搭建引擎内灯光数据采集与模型训练管线</li>
      <li>负责Arc Raider移动端特效资产的整理与规范的制定</li>
      <li>参与制定了一套全新的适用于FPS项目的场景灯光管线，确保室内外曝光正确；开发物理灯具插件，提供DataAsset配置接口，统合大气、后处理、TOD与灯光配置流程</li>
    </ul>
  </div>
</div>

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">藤库网络科技有限公司</span>
    <span class="work-date">2025.08 — 2025.10</span>
  </div>
  <div class="work-role">TATD组 · 技术美术实习生</div>
  <div class="work-desc">
    <ul>
      <li>参与项目代号One Up，在项目既定资产规范下协助完成外部资产的入库</li>
      <li>开发并维护引擎内贴图通道合并映射工具和场景材质覆写扫描工具</li>
    </ul>
  </div>
</div>

# Education

<div class="edu-grid">
  <div class="edu-card">
    <div class="edu-badge"><img src="/img/logo-shu.png" alt="上海大学"></div>
    <div class="edu-info">
      <div class="edu-name">上海大学</div>
      <div class="edu-major">数字媒体创意工程 · 硕士</div>
      <div class="edu-date">2024 — 2027</div>
    </div>
  </div>
  <div class="edu-card">
    <div class="edu-badge"><img src="/img/logo-suibe.png" alt="上海对外经贸大学"></div>
    <div class="edu-info">
      <div class="edu-name">上海对外经贸大学</div>
      <div class="edu-major">数据科学与大数据技术 · 本科</div>
      <div class="edu-date">2020 — 2024</div>
    </div>
  </div>
</div>

# Portfolio

## 可控视频镜头预演生成系统（ECCV 2026）
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/unity.mp4"></video>
基于Unity搭建了一套完整的虚拟相机数据合成管线，包括三种常见相机数据的timeline烘焙工具，并完成了节点式分镜视频生成系统的开发
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/teaser.mp4"></video>
![](/images/folio/Camera/method.png)
以一作身份在 ECCV 2026（CV三大顶会之一）发表相关成果。研究如何将引擎内的镜头预演与现有视频生成大模型相结合，使视频生成工作流更可控。负责课题项目主要功能的实现，涉及：Unity内LLM交互生成剧本与拍摄方案（RAG/Schema结构化）、节点式GUI编辑器、3D相机轨迹数据集构建、基于自回归和Diffusion的轨迹生成模型训练、基于DPO的轨迹后训练

## UE5 AI 智能打光系统
### Agentic Pipeline
HDBSCAN语义聚类初步分组，由聚类Agent推理后，交由Grounding DINO+Line Trace，实现逻辑光源的精确定位。Team Agent编排避免上下文膨胀
### 数据驱动 Pipeline
<video class="folio-video" controls preload="metadata" src="/images/folio/Light/灯光数据驱动demo.mp4"></video>
腾讯IEG实习期间独立负责。SIGGRAPH 2027 Work In Progress
![](/images/folio/Light/Pipeline.png)
使用LumiNet或GPT Img 2等图像生成模型，将参考图打光风格迁移到未打光场景的Unlit渲染结果上，再辅以GBuffer几何信息，共同交由后续灯光参数提取模型重建出引擎内显式灯光参数从零搭建引擎内灯光数据采集与模型训练管线，实现AI辅助打光
![](/images/folio/Light/Extractor.png)
图像灯光参数提取模型需要训练，为此我们从零搭建了灯光数据采集管线，包括但不限于Gbuffer、不同种类的灯光Component参数，通过Jitter & OLAT数据增强实现Scaling Up
模型整体设计为DETR-like Extractor，Coarse2Fine双阶段训练策略，通过匈牙利匹配计算损失以适应非定长无序集合的预测。目前数据采集仍在进行中，但模型本身能力已完成初步验证

## FPS Gameplay
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/FPS.mp4"></video>
从零实现伤害计算、换弹、受击/后坐力反馈等基础FPS gameplay逻辑
基础动画逻辑、动画混合Aimpose以及5种枪支的不同设计
完整的健康系统，Niagara Blood Decal（环境溅血），UMG屏幕血渍 / 受击方位指示器
RPC网络同步，第一人称手臂&第三人称身体同时开发，动画/特效/音效 多播
荒野大镖客2-死神之眼：
技能开启/结束 后处理动画、Time Dilation
维护FHitResult TQueue队列，实现稳定的客户端标记UI与执行逻辑；服务端&客户端计时器句柄确保动画正确执行

## UE5 场景灯光
### TOD系统
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/TOD.mp4"></video>
统合物理大气、程序化天空球、 PP曝光控制；提供规范化的管理流程

### 物理灯具插件
适用于FPS项目的场景灯光管线，确保室内外曝光正确；物理灯具插件提供DataAsset配置接口，统合大气、后处理、TOD与灯光配置流程

## 物理场植被交互
使用单层RT模拟质点弹簧场，材质采样模拟结果做WPO，实现更加自然的弯折回弹
沿植被茎秆应用指数衰减，极大改善植被WPO撕扯问题

## VFX 作品
### 黑Saber Excalibur
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/BlackSaber1.mp4"></video>
程序化+贴图黑白闪、 Modulate假光、 Houdini地裂

### 冰系/水晶
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/Sonetto.mp4"></video>
晶体材质、 样条曲线自定义粒子带、色调分离、 冲击波、法阵

### Tutorial Works
#### 陨石 & 火龙卷
![](/images/folio/VFX/Tutorial/陨石_火龙卷.gif)
视差陨石坑，后期模糊，技能联动，斜切UV...
#### 落雷 & 电弧
![](/images/folio/VFX/Tutorial/落雷.gif)
![](/images/folio/VFX/Tutorial/电弧.gif)
Ribbon，直线场，伤害异步，Event拖尾...
#### 冰锥 & 歼灭
![](/images/folio/VFX/Tutorial/冰锥_歼灭.gif)
视差冰面，SSS冰锥，复杂索敌逻辑，Spawn Group...

## 卡通渲染
### UE5.7修改源码定制卡通渲染
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/Render.mp4"></video>
新增自定义 Shading Model，定制实现 Ramp Atlas阴影过渡、ILM AO / Specular
头发分层 Matcap，Rim Light等常见卡通渲染特性
新增R16 G16 B16 A16  Toon Buffer，自定义MRT Payload，用于向
Deferred Ligting Pass传递数据做后续光照计算
球形视差眼睛渲染，带AO修正面部SDF阴影（Work In Progress）
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/描边.mp4"></video>
将切线空间平滑法线与曲率Bake进模型UV2&UV3，引擎右键菜单集成Bake工具
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/GI1.mp4"></video>
定制修改全局光照，替代球谐，通过修改Lumen抹平法线模拟低频GI，降低暗部塑料感

### Unity URP - 仿原神渲染
![](/images/folio/VFX/Tutorial/甘雨仿原神渲染.gif)
Ramp阴影过渡，屏幕空间等距边缘光，背面法线外扩描边，SDF面部阴影...



## 其他
### 护盾受击效果
![](/images/folio/shield_hit.gif)
WPO，蓝图受击响应逻辑

### 基于学习的特效智能LOD生成方案研究
![](/images/folio/NiagaraAutoLod.gif)
项目由腾讯IEG引擎图形学远程课题实践活动发起。通过该项目初步对深度学习和强化学习相关概念进行了一定程度的学习和探索，了解到了特效制作过程中的一些性能评判标准，也借此尝试了部分理论的建模，并在此过程中从零到一学习了UE5插件开发的相关知识，最后成功实现了如图所示的Niagara批量添加LOD模块的功能（Slate编写等）

### C++软光追渲染器
![](/images/folio/GAMES101_PathTracing.png)
![](/images/folio/In_One_Weekend_spp=100_small.png)
![](/images/folio/The_Next_Week_Final_spp=1024_small.png)
跟随 GAMES101 的课程进度，独立完成了BVH和蒙特卡洛微表面的实现，后通过 Peter Shirely 手写光追系列教程完成了整个渲染器的搭建，并在此基础上实现了 Tone Mapping 和多线程加速

### ShaderToy 练习
![](/images/folio/ShaderToy.gif)
