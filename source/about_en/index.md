---
title: Personal Info
date: 2024-01-02 20:48:25
type: "about_en"
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
}
.skill-card .skill-icon img {
  width: 24px;
  height: 24px;
  object-fit: contain;
  display: block;
}
.skill-card .skill-name {
  font-size: 0.9em;
  font-weight: 600;
  flex-shrink: 0;
  line-height: 24px;
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
}
.edu-card .edu-badge img {
  width: 56px;
  height: 56px;
  object-fit: contain;
  display: block;
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
</style>

# About Me
* Began learning Technical Artist skills (AI/VFX/Rendering/Tools) since 2022. Self-completed GAMES101 and GAMES202, documenting the journey on Zhihu
* Published a paper on controllable video camera preview generation system at ECCV 2026 as first student author
* IELTS 7.0, able to read cutting-edge English literature and technical docs without barriers
* Solid foundations in mathematical statistics, closely following AIGC and 3D vision developments
* Tech Otaku with strong self-drive, able to quickly absorb new knowledge and apply it. Love researching implementation principles of in-game VFX
* Hobbies: finger-style / electric guitar, ACGN enthusiast, Kigurumi, photography

# Skills

<div class="skills-grid">
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" alt="C#"></span><span class="skill-name">C#</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" alt="HLSL"></span><span class="skill-name">Cg/HLSL</span><div class="skill-track"><div class="skill-fill" style="width:85%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python"></span><span class="skill-name">Python</span><div class="skill-track"><div class="skill-fill" style="width:75%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg" alt="C++"></span><span class="skill-name">C++</span><div class="skill-track"><div class="skill-fill" style="width:60%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/unrealengine/unrealengine-original.svg" alt="UE5"></span><span class="skill-name">UE5</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/unity/unity-original.svg" alt="Unity"></span><span class="skill-name">Unity</span><div class="skill-track"><div class="skill-fill" style="width:80%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/blender/blender-original.svg" alt="Blender"></span><span class="skill-name">Blender</span><div class="skill-track"><div class="skill-fill" style="width:55%"></div></div></div>
<div class="skill-card"><span class="skill-icon"><svg viewBox="0 0 24 24" width="24" height="24" fill="#59ADB8" xmlns="http://www.w3.org/2000/svg"><path d="M0 19.635V24h3.824A8.662 8.662 0 0 1 0 19.635zm16.042-4.555c0-4.037-3.253-7.92-8.111-8.089C4.483 6.873 1.801 8.136 0 10.005v4.209c1.224-3.549 4.595-5.158 7.419-5.128 3.531.041 6.251 2.703 6.275 5.72 0 2.878-1.183 4.992-4.436 5.516-1.774.296-4.548-.754-4.436-3.434.065-1.381 1.138-2.162 2.366-2.106-1.207 1.618.39 2.801 1.52 2.561a2.51 2.51 0 0 0 1.966-2.502c0-1.017-.958-2.662-3.333-2.6-2.936.068-4.785 2.183-4.85 4.797-.071 3.28 3.007 5.457 6.174 5.483 4.633.059 7.395-2.984 7.377-7.441zM0 0v6.906a12.855 12.855 0 0 1 7.931-2.609c6.801 0 11.134 4.762 11.131 10.765 0 4.17-1.946 7.308-4.995 8.938H24V0H0z"/></svg></span><span class="skill-name">Houdini</span><div class="skill-track"><div class="skill-fill" style="width:45%"></div></div></div>
</div>

# Work Experience

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">NetEase Thunder Fire · Fuxi AI Lab</span>
    <span class="work-date">2026.05 — Present</span>
  </div>
  <div class="work-role">Decision Intelligence Group · AI Algorithm Intern</div>
  <div class="work-desc">
    <ul>
      <li>Participated in Naraka: Bladepoint AI Bot R&D, responsible for upper-level script mining — extracting reusable tactical patterns from game recordings</li>
      <li>Built a mining pipeline based on temporal knowledge graphs and clustering; Agent queries the graph to generate scripts for match deployment</li>
    </ul>
  </div>
</div>

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">Tencent IEG · Interactive Entertainment Group</span>
    <span class="work-date">2025.11 — 2026.05</span>
  </div>
  <div class="work-role">Domestic Publishing · Eco Development · TA Intern</div>
  <div class="work-desc">
    <ul>
      <li><strong>Independently led UE5 AI smart lighting system R&D</strong>, built in-engine lighting data collection and model training pipeline from scratch</li>
      <li>Responsible for Arc Raider mobile VFX asset cleanup and specification drafting</li>
      <li>Co-developed a new FPS scene lighting pipeline ensuring correct indoor/outdoor exposure; built a physical light fixture plugin with DataAsset config interface, unifying atmosphere, post-processing, TOD and lighting config workflow</li>
    </ul>
  </div>
</div>

<div class="work-entry">
  <div class="work-header">
    <span class="work-company">Tengku Network Technology Co., Ltd.</span>
    <span class="work-date">2025.08 — 2025.10</span>
  </div>
  <div class="work-role">TATD Group · TA Intern</div>
  <div class="work-desc">
    <ul>
      <li>Participated in Project One Up, assisted with external asset onboarding under project specifications</li>
      <li>Developed and maintained in-engine texture channel merging/mapping tools and scene material override scanning tools</li>
    </ul>
  </div>
</div>

# Education

<div class="edu-grid">
  <div class="edu-card">
    <div class="edu-badge"><img src="/img/badge-shu.svg" alt="Shanghai University"></div>
    <div class="edu-info">
      <div class="edu-name">Shanghai University</div>
      <div class="edu-major">Digital Media Creative Engineering · M.Sc.</div>
      <div class="edu-date">2024 — 2027</div>
    </div>
  </div>
  <div class="edu-card">
    <div class="edu-badge"><img src="/img/badge-suibe.svg" alt="SUIBE"></div>
    <div class="edu-info">
      <div class="edu-name">Shanghai University of International Business and Economics</div>
      <div class="edu-major">Data Science & Big Data Technology · B.Sc.</div>
      <div class="edu-date">2020 — 2024</div>
    </div>
  </div>
</div>

# Portfolio

## Shield Hit Effect
![](/images/folio/shield_hit.gif)
WPO, bluprint logics of shield-hit response

## Learning-Based Intelligent LOD Generation for VFX
![](/images/folio/NiagaraAutoLod.gif)
Initiated by Tencent IEG engine graphics remote project. Explored deep learning and reinforcement learning concepts, VFX performance criteria, theoretical modeling, and UE5 plugin development (Slate UI). Successfully implemented batch Niagara LOD module addition

## C++ Software Ray Tracing Renderer
![](/images/folio/GAMES101_PathTracing.png)
![](/images/folio/In_One_Weekend_spp=100_small.png)
![](/images/folio/The_Next_Week_Final_spp=1024_small.png)
Followed GAMES101 course, implemented BVH and Monte-Carlo microsurface, then completed the renderer via Peter Shirley's Ray Tracing series with Tone Mapping and multi-threading

## ShaderToy Practice
![](/images/folio/ShaderToy.gif)

## Controllable Video Camera Preview Generation (ECCV 2026)
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/teaser.mp4"></video>
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/unity.mp4"></video>
![](/images/folio/Camera/method.png)
Published at ECCV 2026 as first student author. Research on combining in-engine camera preview with video generation models for controllable workflows. Responsible for: Unity LLM interaction (RAG/Schema), node-based GUI editor, 3D camera trajectory dataset, autoregressive & Diffusion trajectory generation, DPO post-training

## UE5 AI Smart Lighting System
![](/images/folio/Light/Pipeline.png)
![](/images/folio/Light/Extractor.png)
<video class="folio-video" controls preload="metadata" src="/images/folio/Light/灯光数据驱动demo.mp4"></video>
Independently developed during Tencent IEG internship. Built in-engine lighting data collection and model training pipeline from scratch

## UE5 Scene Lighting Pipeline & Physical Light Plugin
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/FPS.mp4"></video>
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/TOD.mp4"></video>
FPS scene lighting pipeline ensuring correct indoor/outdoor exposure; physical light fixture plugin with DataAsset config interface, unifying atmosphere, post-processing, TOD and lighting config

## VFX Works
### Black Saber VFX
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/黑Saber1.mp4"></video>
### Sonetto VFX
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/Sonetto.mp4"></video>

### VFX Tutorial
A series of advanced effects using UE4 Niagara, materials and blueprints
#### Fire Meteor & Hell Attack
![](/images/folio/VFX/Tutorial/陨石_火龙卷.gif)
Crater by parallax occlusion, radial blur with stencil test, combo logic, UV shearing
#### Thunder & Lightning Bolt
![](/images/folio/VFX/Tutorial/落雷.gif)
![](/images/folio/VFX/Tutorial/电弧.gif)
Line field, asynchronous damage, ribbon tail with Niagara event
#### Ice Spike & Annihilate
![](/images/folio/VFX/Tutorial/冰锥_歼灭.gif)
SSS ice material, complex logic for searching enemy, Spawn Group
#### Unity URP - Genshin Impact Character Shading
![](/images/folio/VFX/Tutorial/甘雨仿原神渲染.gif)
Ramp shadow, SDF face shadow, screen space rim light, backface normal outline

## Unity URP Toon Rendering
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/描边.mp4"></video>
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/GI1.mp4"></video>
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/Render.mp4"></video>
