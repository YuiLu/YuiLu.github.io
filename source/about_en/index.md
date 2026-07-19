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
  <a href="/about_cn/">简体中文</a>
  <a href="/about_en/" class="active">English</a>
</div>

</div>

* Started systematically learning skills at the intersection of game graphics and AI since 2022 (Rendering / AI / VFX / Toolchain)
* Published work on a controllable video camera preview generation system at ECCV 2026 as first student author
* Good English reading and writing skills (IELTS 7.0), able to read cutting-edge English literature and technical docs without barriers
* Solid foundations in mathematical statistics and data science, with experience in model training and dataset construction & processing
* A certain knowledge reserve in computer graphics, familiar with basic data structures and algorithm principles
* Tech otaku with strong self-drive and learning initiative, able to quickly absorb new knowledge and apply it in practice. Love researching the implementation principles of in-game special effects
* Familiar with common toon rendering techniques, having attempted to land and implement effects in both Unity and UE5
* Hobbies: ACGN enthusiast, Kigurumi, photography, fingerstyle guitar<span class='heimu' title="You know too much">(listen only, don't play)</span> / electric guitar, and everything related to computer graphics

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
    <div class="edu-badge"><img src="/img/logo-shu.png" alt="Shanghai University"></div>
    <div class="edu-info">
      <div class="edu-name">Shanghai University</div>
      <div class="edu-major">Digital Media Creative Engineering · M.Sc.</div>
      <div class="edu-date">2024 — 2027</div>
    </div>
  </div>
  <div class="edu-card">
    <div class="edu-badge"><img src="/img/logo-suibe.png" alt="SUIBE"></div>
    <div class="edu-info">
      <div class="edu-name">Shanghai University of International Business and Economics</div>
      <div class="edu-major">Data Science & Big Data Technology · B.Sc.</div>
      <div class="edu-date">2020 — 2024</div>
    </div>
  </div>
</div>

# Portfolio

## Controllable Video Camera Preview Generation (ECCV 2026)
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/unity.mp4"></video>
Built a complete virtual camera data synthesis pipeline on Unity, including timeline baking tools for three common camera data types, and developed a node-based storyboard video generation system
<video class="folio-video" controls preload="metadata" src="/images/folio/Camera/teaser.mp4"></video>
![](/images/folio/Camera/method.png)
Published at ECCV 2026 (one of the top three CV conferences) as first author. Research on combining in-engine camera preview with video generation models for controllable workflows. Responsible for the main features of the project: Unity LLM interaction for script & shooting plan generation (RAG/Schema structured), node-based GUI editor, 3D camera trajectory dataset construction, autoregressive & Diffusion-based trajectory generation model training, DPO-based trajectory post-training

## UE5 AI Smart Lighting System
### Agentic Pipeline
HDBSCAN semantic clustering for preliminary grouping; after reasoning by the clustering Agent, Grounding DINO + Line Trace achieves precise localization of logical light sources. Team Agent orchestration avoids context bloat
### Data-Driven Pipeline
<video class="folio-video" controls preload="metadata" src="/images/folio/Light/灯光数据驱动demo.mp4"></video>
Independently led during Tencent IEG internship. SIGGRAPH 2027 Work In Progress
![](/images/folio/Light/Pipeline.png)
Using image generation models such as LumiNet or GPT Img 2 to transfer the lighting style of a reference image onto the Unlit render of an un-lit scene, then combined with GBuffer geometry information, fed into the subsequent lighting parameter extraction model to reconstruct explicit in-engine light parameters. Built the in-engine lighting data collection and model training pipeline from scratch for AI-assisted lighting
![](/images/folio/Light/Extractor.png)
The image-to-lighting-parameter extraction model requires training, so we built a lighting data collection pipeline from scratch, including but not limited to GBuffer and various light Component parameters, achieving Scaling Up via Jitter & OLAT data augmentation
The model is designed as a DETR-like Extractor with a Coarse2Fine two-stage training strategy, using Hungarian matching to compute loss for predicting variable-length unordered sets. Data collection is still ongoing, but the model's capability has been preliminarily validated

## FPS Gameplay
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/FPS.mp4"></video>
Implemented basic FPS gameplay logic from scratch: damage calculation, reloading, hit / recoil feedback
Basic animation logic, animation blending with Aim Offset, and distinct designs for 5 weapons
Complete health system, Niagara Blood Decal (environmental blood splatter), UMG screen blood stains / hit-direction indicator
RPC network replication; first-person arms & third-person body developed simultaneously, with multicast animation / VFX / audio
Red Dead Redemption 2 - Dead Eye:
Skill activation/deactivation post-process animation, Time Dilation
Maintains an FHitResult TQueue to achieve stable client-side marking UI and execution logic; server & client timer handles ensure correct animation execution

## UE5 Scene Lighting
### TOD System
<video class="folio-video" controls preload="metadata" src="/images/folio/260710/TOD.mp4"></video>
Unifies physical atmosphere, procedural sky sphere, and PP exposure control; provides a standardized management workflow

### Physical Light Fixture Plugin
Scene lighting pipeline for FPS projects ensuring correct indoor/outdoor exposure; the physical light fixture plugin provides a DataAsset config interface, unifying atmosphere, post-processing, TOD and lighting config workflow

## Physics-Field Foliage Interaction
Uses a single-layer RT to simulate a mass-spring field; material samples the simulation result for WPO, achieving more natural bending and rebound
Applies exponential decay along the foliage stem, greatly improving the WPO tearing issue

## VFX Works
### Black Saber Excalibur
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/BlackSaber1.mp4"></video>
Procedural + texture black-white flash, Modulate fake light, Houdini ground crack

### Ice / Crystal
<video class="folio-video" controls preload="metadata" src="/images/folio/VFX/Sonetto.mp4"></video>
Crystal material, spline-based custom particle ribbon, posterization, shockwave, magic circle

### Tutorial Works
#### Fire Meteor & Hell Attack
![](/images/folio/VFX/Tutorial/陨石_火龙卷.gif)
Parallax crater, post blur, combo logic, UV shearing...
#### Thunder & Lightning Bolt
![](/images/folio/VFX/Tutorial/落雷.gif)
![](/images/folio/VFX/Tutorial/电弧.gif)
Ribbon, line field, asynchronous damage, Event tail...
#### Ice Spike & Annihilate
![](/images/folio/VFX/Tutorial/冰锥_歼灭.gif)
Parallax ice surface, SSS ice spike, complex enemy-searching logic, Spawn Group...

## Toon Rendering
### UE5.7 Source-Modified Custom Toon Rendering
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/Render.mp4"></video>
Added a custom Shading Model with Ramp Atlas shadow transition, ILM AO / Specular
Layered hair Matcap, Rim Light and other common toon rendering features
Added an R16 G16 B16 A16 Toon Buffer with custom MRT Payload to pass data to the Deferred Lighting Pass for subsequent lighting calculation
Spherical parallax eye rendering, with AO-corrected facial SDF shadow (Work In Progress)
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/描边.mp4"></video>
Bakes tangent-space smoothed normals and curvature into the model's UV2 & UV3; Bake tool integrated into the engine right-click menu
<video class="folio-video" controls preload="metadata" src="/images/folio/Toon/GI1.mp4"></video>
Custom-modified global illumination replacing spherical harmonics; flattens normals by modifying Lumen to simulate low-frequency GI, reducing the plastic look in dark areas

### Unity URP - Genshin Impact Character Shading
![](/images/folio/VFX/Tutorial/甘雨仿原神渲染.gif)
Ramp shadow transition, screen-space equidistant rim light, backface normal outline, SDF face shadow...

## Others
### Shield Hit Effect
![](/images/folio/shield_hit.gif)
WPO, blueprint hit-response logic

### Learning-Based Intelligent LOD Generation for VFX
![](/images/folio/NiagaraAutoLod.gif)
Initiated by Tencent IEG engine graphics remote project. Explored deep learning and reinforcement learning concepts, learned about VFX performance criteria, attempted theoretical modeling, and learned UE5 plugin development from scratch. Successfully implemented batch Niagara LOD module addition as shown (Slate UI, etc.)

### C++ Software Ray Tracing Renderer
![](/images/folio/GAMES101_PathTracing.png)
![](/images/folio/In_One_Weekend_spp=100_small.png)
![](/images/folio/The_Next_Week_Final_spp=1024_small.png)
Following the GAMES101 course, independently implemented BVH and Monte-Carlo microsurface, then completed the whole renderer via Peter Shirley's Ray Tracing series, adding Tone Mapping and multi-threading on top

### ShaderToy Practice
![](/images/folio/ShaderToy.gif)
