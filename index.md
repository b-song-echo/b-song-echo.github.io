---
layout: default
title: 宋柏君 · 个人简历
description: 清华大学硕士，研究多模态生成、世界模型、表征学习等。
---

![宋柏君的照片](assets/profile.jpg){: .profile-photo }

# 宋柏君 {#top}

**多模态生成 · 世界模型 · 表征学习** ｜ [*查看最新版本*](https://b-song-echo.github.io){:target="_blank" rel="noopener noreferrer"}

[19350669024](tel:+8619350669024) · [b.song.echo@gmail.com](mailto:b.song.echo@gmail.com) · [GitHub](https://github.com/b-song-echo){:target="_blank" rel="noopener noreferrer"} · [Google Scholar](https://scholar.google.com/citations?hl=en&user=azqxpKgAAAAJ){:target="_blank" rel="noopener noreferrer"}

研究多模态生成、世界模型、表征学习，具备从问题定义到模型设计再到大规模训练与评测的实践经验。

---

[教育](#education) · [实习](#internship) · [论文](#publications) · [其他](#misc)
{: .section-nav }

## 教育 {#education}

**清华大学**｜电子信息｜硕士｜袁春教授指导  
2024.09 – 2027.06

**大连理工大学**｜力学｜本科  
2020.09 – 2024.06

## 实习 {#internship}

**美团**｜多模态算法科研实习生（校企合作）｜点评·智能创作团队  
2025.07 – 至今  
获评**美团优秀科研实习生**

### WorldRoll：World Model Data & Post-Training

*第一作者，AAAI 2027 Under Review｜2025.08 – 2026.07*

- **独立设计并实现**面向 I2V 模型的 world rollout 后训练数据 pipeline：将相机位姿/轨迹转化为**首帧 + 自然语言**监督，使模型在训练/推理阶段可仅通过自然语言实现精确的相机控制。
- 构建 **三源 60K 视频数据**：融合带相机位姿的真实视频（PA）、场景动态的真实视频（DR）与 **HY-WorldPlay** 生成的视频（TG）；使用 **Qwen3.6-27B** 完成scene / subject / camera 的结构化标注与 group-balanced 质量过滤。
- 完成 **LTX-Video-2B** 与 **CogVideoX-Fun-2B** 在该数据集上的微调：两者 WorldScore Static / Dynamic 分别提升 **8.1% / 5.5%** 与 **8.8% / 5.9%**，WorldModelBench 提升 **5.2% / 4.9%**；完成 data composition、LoRA rank、data / training scaling 等实验。
- **大规模训练工程：** 完成 ****HunyuanVideo** 在 241 帧 / 720p 视频上的**多机 + FSDP + USP（Ulysses + RingAttention）** 训练。
- **垂域扩展：** 正将上述数据 pipeline 迁移至**大众点评商家 I2V 场景**，构建垂域训练数据，支持门店图 + 预设 prompt 的短视频生成。

### RibbonTok：Visual Tokenization for AR Generation

*第一作者，AAAI 2027 Under Review｜2025.08 – 2026.07*

- **独立设计并实现**面向自回归图像生成的 resolution-consistent、离散 1D、可变长度的 tokenizer：将图像编码为 **coarse-to-fine causal** 的 token 序列，支持任意前缀独立解码重建，并将 **token budget（logical description）与 output grid（physical resolution）解耦**，直接降低自回归生成的开销。
- 提出 **causal masked-register ViT + stacked directional codebooks + rectified-flow DiT**；提出全新训练约束 **coalesce matching**：在 VQ 时，对跨分辨率 triplet 视图的前缀表征进行显式约束，使相同逻辑内容跨物理分辨率保持一致。
- 训练三种规模（300M / 1B / 2.5B）的 tokenizer，后者在 ImageNet 重建达到 **rFID 1.04 / PSNR 19.36 / SSIM 0.582**；完成结构/训练模块消融与 codebook 分析等实验。
- 训练两种规模（1B、3B）的 Llama-style 自回归生成模型，后者相比 **LlamaGen-3B** 仅用其 1/8 的 token 数量取得了更佳效果，在 ImageNet 达到 **gFID 1.43 / IS 348.8**，同时实现了 **>2× 的端到端加速**。

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
