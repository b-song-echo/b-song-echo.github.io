---
layout: default
title: 宋柏君 · 个人简历
description: 清华大学硕士，研究多模态生成、世界模型、表征学习等。
---

<div class="resume-content" data-resume-language="zh-CN" data-document-title="宋柏君 · 个人简历" lang="zh-CN" markdown="1">

![宋柏君的照片](assets/profile.jpg){: .profile-photo }

# 宋柏君 {#top}

**多模态生成 · 世界模型 · 表征学习** ｜ [*查看最新版本*](https://b-song-echo.github.io){:target="_blank" rel="noopener noreferrer"}

[19350669024](tel:+8619350669024) · [b.song.echo@gmail.com](mailto:b.song.echo@gmail.com) · [GitHub](https://github.com/b-song-echo){:target="_blank" rel="noopener noreferrer"} · [Google Scholar](https://scholar.google.com/citations?hl=en&user=azqxpKgAAAAJ){:target="_blank" rel="noopener noreferrer"}

研究多模态生成、世界模型、表征学习，具备从问题定义到模型设计再到大规模训练与评测的实践经验。

---

[教育](#education) · [实习](#internship) · [论文](#publications) · [其他](#misc)
{: .section-nav }

## 教育 {#education}

2024.09 – 2027.06｜**清华大学**｜电子信息｜硕士｜袁春教授指导

2020.09 – 2024.06｜**大连理工大学**｜力学｜本科

## 实习 {#internship}

2025.07 – 至今｜**美团**｜多模态算法科研实习生（校企合作）｜点评·智能创作<br>
获评**美团优秀科研实习生**

### WorldRoll：World Model Data & Post-Training

*第一作者，AAAI 2027 Under Review｜2025.08 – 2026.07*

- **独立设计并实现**面向 I2V 模型的 world rollout 后训练数据 pipeline：将相机位姿/轨迹信号转化为以**首帧 + 自然语言**为条件的监督数据，使模型在训练和推理阶段仅依赖自然语言即可实现精细的相机控制。
- 构建包含 **120K 视频的三源数据集**：融合带相机位姿的真实视频（PA）、包含场景动态的真实视频（DR）与教师世界模型（**HY-WorldPlay**）生成的视频（TG）；使用 **Qwen3.6-27B** 对真实视频的 scene / subject / camera 进行结构化标注，并采用 group-balanced 策略进行质量过滤，得到 **60k** 高质量训练数据。
- **位姿量化与语言监督：** 将相机位姿序列转化为 **motion-unit statistics**，并通过 prompt template 提供解释和标注的规则。引导 VLM 生成带旋转角度 / 位移幅值的相机运动描述。
- 完成 **LTX-Video-2B** 与 **CogVideoX-Fun-2B** 的微调。两者的 WorldScore Static / Dynamic 分别提升 **8.1% / 5.5%** 与 **8.8% / 5.9%**，WorldModelBench 分别提升 **5.2% / 4.9%**；完成 data composition、LoRA rank、data / training scaling 等实验。
- **大规模训练工程：** 实现 **HunyuanVideo** 在 241 帧 / 720p 视频上的**多机 + FSDP + USP（Ulysses + RingAttention）**训练。
- **垂域扩展：** 应用至**大众点评商家 I2V 场景**，构建垂域训练数据，支持门店图像 + 预设 prompt 的短视频生成。

### RibbonTok：Visual Tokenization for AR Generation

*第一作者，AAAI 2027 Under Review｜2025.08 – 2026.07*

- **独立设计并实现**面向自回归图像生成、具备 resolution consistency、离散 1D 表征与可变长度编码能力的 tokenizer。该模型将图像编码为 **coarse-to-fine causal token 序列**，支持对任意前缀进行独立解码与重建，并将 **token budget（logical description）与 output grid（physical resolution）解耦**，直接降低自回归生成开销。
- 设计 **causal masked-register ViT + stacked directional codebooks + rectified-flow DiT**，并提出全新训练约束 **coalesce matching**：在 VQ 阶段显式约束跨分辨率 triplet 视图的前缀表征，使相同逻辑内容在不同物理分辨率下保持一致。
- **自回归生成离散 token：** 每个 token 由 **4 个独立 codes 组成**，每个 code 对应一个 **16k** 大小的 codebook；自回归模型每次由 4 个 heads 并行预测 4 个 codes。
- 训练 300M / 1B / 2.5B 三种规模的 tokenizer，其中 2.5B 模型在 ImageNet 重建达到 **rFID 1.04 / PSNR 19.36 / SSIM 0.582**；完成结构与训练策略的消融及 codebook 分析等实验，模块全部有效，且 codebook 利用率达到 **0.97**。
- 训练 1B / 3B 两种规模的 Llama-style 自回归生成模型，其中 3B 模型仅使用 **LlamaGen-3B** 约 1/8 的 token 数量即取得更优效果，在 ImageNet 达到 **gFID 1.43 / IS 348.8**，同时实现 **>2× 端到端加速**。

## 论文 {#publications}

1. WorldRoll: From Privileged Camera Trajectories to Pose-Free World Rollouts  
   **第一作者**，AAAI 2027 Under Review｜[论文 PDF](assets/WorldRoll_main.pdf){:target="_blank" rel="noopener noreferrer"} · [补充材料 PDF](assets/WorldRoll_supp.pdf){:target="_blank" rel="noopener noreferrer"}

2. RibbonTok: Multi-Resolution, Single-Stream, and Adaptive-Length Tokenization for Autoregressive Image Generation  
   **第一作者**，AAAI 2027 Under Review｜[论文 PDF](assets/RibbonTok_main.pdf){:target="_blank" rel="noopener noreferrer"} · [补充材料 PDF](assets/RibbonTok_supp.pdf){:target="_blank" rel="noopener noreferrer"}

3. M3Time: LLM-Enhanced Multi-Modal, Multi-Scale, and Multi-Frequency Multivariate Time Series Forecasting  
   **共同第一作者**，AAAI 2026 Poster｜[AAAI 论文页](https://ojs.aaai.org/index.php/AAAI/article/view/39383){:target="_blank" rel="noopener noreferrer"} · [论文 PDF](assets/M3Time.pdf){:target="_blank" rel="noopener noreferrer"}

## 其他 {#misc}

- **编程：** 掌握 **Python、C++、PyTorch**；了解 **Triton、CUDA、Metal**。
- **英语：** **TOEFL 106**（L30 / R29 / S24 / W23），CET-6 624，CET-4 647。
- **绩点：** 本科 3.4 / 4.0，硕士 3.9 / 4.0。
- **竞赛：** 2022 数模国赛省三等奖。

[返回顶部](#top)
{: .back-to-top }

</div>

<div class="resume-content" data-resume-language="en" data-document-title="Baijun Song · Résumé" lang="en" hidden markdown="1">

![Portrait of Baijun Song](assets/profile.jpg){: .profile-photo }

# Baijun Song {#top-en}

**Multimodal Generation · World Models · Representation Learning** · [*View live résumé*](https://b-song-echo.github.io){:target="_blank" rel="noopener noreferrer"}

[+86 193 5066 9024](tel:+8619350669024) · [b.song.echo@gmail.com](mailto:b.song.echo@gmail.com) · [GitHub](https://github.com/b-song-echo){:target="_blank" rel="noopener noreferrer"} · [Google Scholar](https://scholar.google.com/citations?hl=en&user=azqxpKgAAAAJ){:target="_blank" rel="noopener noreferrer"}

Researcher in multimodal generation, world models, and representation learning, with hands-on experience spanning problem formulation, model design, large-scale training, and evaluation.

---

[Education](#education-en) · [Experience](#experience-en) · [Publications](#publications-en) · [Additional](#additional-en)
{: .section-nav }

## Education {#education-en}

Sep 2024 – Jun 2027 · **Tsinghua University** · M.Eng. in Electronic Information · Advisor: Prof. Chun Yuan

Sep 2020 – Jun 2024 · **Dalian University of Technology** · B.Eng. in Mechanics

## Experience {#experience-en}

Jul 2025 – Present · **Meituan** · Research Intern, Multimodal Algorithms (Industry–University Collaboration) · Dianping · Intelligent Creation<br>
Recognized as an **Outstanding Research Intern at Meituan**

### WorldRoll: World Model Data & Post-Training

*First Author · Under Review at AAAI 2027 · Aug 2025 – Jul 2026*

- **Independently designed and implemented** a world-rollout post-training data pipeline for image-to-video models. It converts privileged camera poses and trajectories into supervision conditioned on the **first frame and natural-language instructions**, enabling precise language-only camera control at both training and inference time.
- Built a **120K-video, three-source dataset** combining real videos with camera poses (PA), dynamic real-world videos (DR), and videos generated by the teacher world model **HY-WorldPlay** (TG). Used **Qwen3.6-27B** to annotate scene, subject, and camera attributes in real videos, then applied group-balanced quality filtering to retain **60K** high-quality training samples.
- **Pose quantization and language supervision:** converted camera-pose sequences into **motion-unit statistics** and encoded interpretation and annotation rules in prompt templates, guiding a VLM to describe camera motions with rotation angles and translation magnitudes.
- Fine-tuned **LTX-Video-2B** and **CogVideoX-Fun-2B**, improving WorldScore Static / Dynamic by **8.1% / 5.5%** and **8.8% / 5.9%**, respectively, and WorldModelBench by **5.2% / 4.9%**. Conducted studies on data composition, LoRA rank, and data / training scaling.
- **Large-scale training:** implemented multi-node training of **HunyuanVideo** on 241-frame, 720p videos with **FSDP + USP (Ulysses + RingAttention)**.
- **Domain adaptation:** extended the pipeline to **Dianping merchant I2V generation**, building domain-specific training data for short videos conditioned on merchant images and preset prompts.

### RibbonTok: Visual Tokenization for AR Generation

*First Author · Under Review at AAAI 2027 · Aug 2025 – Jul 2026*

- **Independently designed and implemented** a resolution-consistent tokenizer for autoregressive image generation, featuring discrete 1D representations and adaptive-length encoding. Images are encoded as **coarse-to-fine causal token sequences** whose arbitrary prefixes can be decoded independently. Decoupling the **token budget (logical description) from the output grid (physical resolution)** directly reduces autoregressive generation cost.
- Designed a **causal masked-register ViT, stacked directional codebooks, and rectified-flow DiT**, along with a new training objective, **coalesce matching**. During VQ training, it explicitly aligns prefix representations across triplets of resolutions so the same logical content remains consistent at different physical resolutions.
- **Discrete tokens for autoregressive generation:** each token consists of **four independent codes**, each drawn from a **16K-entry codebook**; four heads predict the codes in parallel at every autoregressive step.
- Trained 300M, 1B, and 2.5B tokenizers. The 2.5B model achieved **rFID 1.04 / PSNR 19.36 / SSIM 0.582** on ImageNet reconstruction. Architecture and training-strategy ablations validated every component, with codebook utilization reaching **0.97**.
- Trained 1B and 3B Llama-style autoregressive generators. Using only about **1/8 as many tokens as LlamaGen-3B**, the 3B model performed better on ImageNet with **gFID 1.43 / IS 348.8**, while delivering **over 2× end-to-end speedup**.

## Publications {#publications-en}

1. WorldRoll: From Privileged Camera Trajectories to Pose-Free World Rollouts<br>
   **First Author** · AAAI 2027 (Under Review) · [Paper](assets/WorldRoll_main.pdf){:target="_blank" rel="noopener noreferrer"} · [Supplementary](assets/WorldRoll_supp.pdf){:target="_blank" rel="noopener noreferrer"}

2. RibbonTok: Multi-Resolution, Single-Stream, and Adaptive-Length Tokenization for Autoregressive Image Generation<br>
   **First Author** · AAAI 2027 (Under Review) · [Paper](assets/RibbonTok_main.pdf){:target="_blank" rel="noopener noreferrer"} · [Supplementary](assets/RibbonTok_supp.pdf){:target="_blank" rel="noopener noreferrer"}

3. M3Time: LLM-Enhanced Multi-Modal, Multi-Scale, and Multi-Frequency Multivariate Time Series Forecasting<br>
   **Co-First Author** · AAAI 2026 Poster · [AAAI Paper Page](https://ojs.aaai.org/index.php/AAAI/article/view/39383){:target="_blank" rel="noopener noreferrer"} · [Paper](assets/M3Time.pdf){:target="_blank" rel="noopener noreferrer"}

## Additional {#additional-en}

- **Programming:** proficient in **Python, C++, and PyTorch**; familiar with **Triton, CUDA, and Metal**.
- **English:** **TOEFL 106** (L30 / R29 / S24 / W23); CET-6 624; CET-4 647.
- **GPA:** 3.4 / 4.0 undergraduate; 3.9 / 4.0 graduate.
- **Competition:** Provincial Third Prize, 2022 China Undergraduate Mathematical Contest in Modeling.

[Back to top](#top-en)
{: .back-to-top }

</div>
