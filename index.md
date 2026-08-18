---
layout: default
title: 宋柏君 · 个人简历
description: 清华大学硕士，研究多模态生成、世界模型、表征学习等。
---

![宋柏君的照片](assets/profile.jpg){: .profile-photo }

# 宋柏君 {#top}

**多模态生成 · 世界模型 · 表征学习**

[19350669024](tel:+8619350669024) · [b.song.echo@gmail.com](mailto:b.song.echo@gmail.com) · [GitHub](https://github.com/b-song-echo){:target="_blank" rel="noopener noreferrer"} · [Google Scholar](https://scholar.google.com/citations?hl=en&user=azqxpKgAAAAJ){:target="_blank" rel="noopener noreferrer"}

专注于多模态生成、世界模型、表征学习，具备从问题定义到模型设计再到大规模训练与评测的完整实践经验。

---

[教育](#education) · [实习](#internship) · [论文](#publications) · [技能](#skills)
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

- **独立设计并实现**面向 I2V 世界模型的数据 pipeline，将相机位姿/轨迹等信号转化为仅依赖**首帧 + 自然语言**的 world rollout 数据，模型在训练或推理阶段可仅通过自然语言实现精确的相机控制。
- 构建**三源数据 pipeline**：融合带相机位姿真实视频、场景动态真实视频、教师世界模型（**HY-WorldPlay**）生成数据；完成基于 VLM（**Qwen3.6-27B**）的标注与筛选，得到 **60K 高质量训练视频**。
- 对 **LTX-Video-2B** 与 **CogVideoX-Fun-2B** 在该数据集上进行 LoRA 微调后，两者在 **WorldScore Static 提升 8.1% / 8.8%，Dynamic 提升 5.5% / 5.9%，WorldModelBench 提升 5.2% / 4.9%**；进行数据组合、数据/训练 scaling 等实验；目前在内部进一步面向大众点评商家垂域场景构建数据。

### RibbonTok：Visual Tokenization for AR Generation

*第一作者，AAAI 2027 Under Review｜2025.08 – 2026.07*

- **独立设计并实现**面向自回归图像生成的多分辨率、单流、可变长度 tokenizer，将图像编码为**coarse-to-fine 的 1D causal token sequence**，其任意前缀序列均可独立被解码重建成多物理分辨率图像。
- 提出模型结构：**causal masked-register ViT、stacked directional codebooks 与 flow DiT**；提出训练方式 **coalesce matching**，显式约束跨分辨率视图的前缀表征，使逻辑图像表征与物理输出分辨率解耦。
- 训练三种规模（300M、1B、2.5B）的 tokenizer，后者在 ImageNet 上取得 **rFID 1.04 @ 256** 重建指标；训练两种规模（1B、3B）的 Llama-style AR 模型，后者在 ImageNet 上仅生成 **32 tokens** 即达到 **gFID 1.43 / IS 348.8** 的生成指标，超越同规模模型（如 LlamaGen-3B）的同时实现 **>2× 端到端加速**。

## 论文 {#publications}

1. [**WorldRoll: From Privileged Camera Trajectories to Pose-Free World Rollouts**](assets/WorldRoll_main.pdf){:target="_blank" rel="noopener noreferrer"}  
   **第一作者**，AAAI 2027 Under Review｜[论文 PDF](assets/WorldRoll_main.pdf){:target="_blank" rel="noopener noreferrer"} · [补充材料 PDF](assets/WorldRoll_supp.pdf){:target="_blank" rel="noopener noreferrer"}

2. [**RibbonTok: Multi-Resolution, Single-Stream, and Adaptive-Length Tokenization for Autoregressive Image Generation**](assets/RibbonTok_main.pdf){:target="_blank" rel="noopener noreferrer"}  
   **第一作者**，AAAI 2027 Under Review｜[论文 PDF](assets/RibbonTok_main.pdf){:target="_blank" rel="noopener noreferrer"} · [补充材料 PDF](assets/RibbonTok_supp.pdf){:target="_blank" rel="noopener noreferrer"}

3. [**M3Time: LLM-Enhanced Multi-Modal, Multi-Scale, and Multi-Frequency Multivariate Time Series Forecasting**](assets/M3Time.pdf){:target="_blank" rel="noopener noreferrer"}  
   **共同第一作者**，AAAI 2026 Poster｜[论文 PDF](assets/M3Time.pdf){:target="_blank" rel="noopener noreferrer"}

## 技能 {#skills}

- **模型：** 熟练掌握 **PyTorch**；熟悉 **Transformers**、**Diffusers** 等框架；实现过各种 **DiT 结构**，如类似 HunyuanVideo 的 MMDiT、类似 Wan 的 DiT；实现过各种**位置编码**，如类似 Qwen 的 MMRoPE；实现过**多模态序列切分/聚合**，如针对 MoE-FFN、SP 等场景；熟悉多种 **Attention 变体**，如 FlashAttention、SageAttention。
- **训练/推理：** 掌握 **FSDP**、**USP**（Ulysses + RingAttention）、Gradient Checkpointing 等训练技巧；熟悉 **PyTorch Distributed**、**Accelerate**、**DeepSpeed** 等训练框架，实操过 **HunyuanVideo**（8B）在 241 帧 720p 视频上的多机（2 × 8 A100）+ FSDP + USP + Gradient Checkpointing 训练；熟悉 **vLLM** 等推理框架；掌握多模态/多对话的请求处理；熟悉 DiffSynth-Studio、VideoX-Fun 等第三方仓库。
- **数据：** 多模态数据下载、管理、清洗；数据生成、标注、筛选、分析等。
- **编程：** 掌握 **Python**、**C++**；熟悉 Swift、C#；了解 **Triton**、CUDA、Metal。
- **英语：** **TOEFL 106**（L30 / R29 / S24 / W23），CET-6 624，CET-4 647。

[返回顶部](#top)
{: .back-to-top }
