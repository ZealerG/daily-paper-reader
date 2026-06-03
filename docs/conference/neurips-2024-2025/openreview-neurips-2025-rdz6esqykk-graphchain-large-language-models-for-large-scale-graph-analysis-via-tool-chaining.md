---
title: "GraphChain: Large Language Models for Large-scale Graph Analysis via Tool Chaining"
title_zh: GraphChain：通过工具链使大型语言模型进行大规模图分析
authors: "Chunyu Wei, Wenji Hu, Xingjia Hao, Xin Wang, Yifan Yang, Yunhai Wang, Yang Tian, Yueguo Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Rdz6ESQYkK"
tags: ["query:graph-rl"]
score: 7.0
evidence: 强化学习用于图分析中的工具序列生成
tldr: 该论文提出GraphChain框架，利用强化学习（渐进图蒸馏）使LLM能够通过动态工具链分析大规模图，克服了LLM的上下文限制；同时引入结构自适应测试时适应，提升了图分析性能，展示了强化学习在图结构任务中的有效应用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 640, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 789, \"height\": 656, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1143, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 1223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rdz6esqykk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 1289, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1160, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1013, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 553, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1346, \"height\": 1643, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1346, \"height\": 1593, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1347, \"height\": 1769, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1349, \"height\": 1115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rdz6esqykk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1388, \"height\": 1442, \"label\": \"Table\"}]"
motivation: 大规模图分析对LLM来说面临上下文限制和推理僵化的挑战。
method: 提出渐进图蒸馏的强化学习方法，学习生成工具序列，并结合结构感知测试时适应。
result: 在多个大规模图分析任务上，GraphChain显著优于现有LLM基线和专用方法。
conclusion: 该工作成功将RL与图分析结合，为LLM处理大规模图提供了新范式。
---

## Abstract
Large Language Models (LLMs) face significant limitations when applied to large-scale graphs, struggling with context constraints and inflexible reasoning. We introduce GraphChain, a novel framework enabling LLMs to analyze large graphs by orchestrating dynamic sequences of specialized tools, mimicking human exploratory processes. GraphChain incorporates two core technical contributions: (1) Progressive Graph Distillation, a reinforcement learning approach that learns to generate tool sequences balancing task relevance and intermediate state compression, thereby overcoming LLM context limitations. (2) Structure-aware Test-Time Adaptation (STTA), a mechanism using a lightweight, self-supervised adapter conditioned on graph spectral properties to efficiently adapt a frozen LLM policy to diverse graph structures via soft prompts without retraining. Experiments show GraphChain significantly outperforms prior methods, enabling scalable and adaptive LLM-driven graph analysis.

---

## 论文详细总结（自动生成）

# GraphChain 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：大型语言模型（LLM）在处理大规模图数据时面临两大挑战：
  - **上下文耗尽**：图数据规模巨大（百万节点/边），无法全部放入 LLM 的有限上下文窗口。
  - **推理幻觉**：现有工具学习方法（如 Graph-ToolFormer、GraphForge）依赖于单步工具调用或固定预定义工具，难以处理复杂多步推理，容易产生错误结论。
- **背景**：现有研究分为两类——直接处理（图编码/自然语言描述）和工具学习（单步工具调用），均难以兼顾可扩展性与推理准确性。受人类探索性认知启发（先广泛扫描再逐步聚焦），作者提出动态工具链方法。

## 2. 论文提出的方法论
### 核心思想
- 将大规模图分析建模为**马尔可夫决策过程（MDP）**，LLM 作为智能体通过**动态工具链**逐步调用图处理工具（基于 NetworkX 的 45 个函数），每次工具调用返回自然语言总结和更新后的内存状态，从而压缩信息并保留关键内容。
- 引入两项关键创新：
  - **渐进图蒸馏**：通过强化学习（PPO）训练策略，使其在选择工具序列时**同时最大化任务相关性和最小化内存状态体积**。使用图描述长度（GDL）衡量信息量，并用辅助 LLM 评分器估计相关性，奖励函数包含执行成功、体积缩减和相关性提升三项。
  - **结构感知测试时自适应（STTA）**：针对不同图拓扑，利用图的**拉普拉斯矩阵最小奇异值**作为结构指纹，通过轻量级适配器生成软提示，修改冻结 LLM 策略的输入，无需重新训练即可适应新图。适应目标包括链长度和 KL 散度正则化，使用 REINFORCE 优化。
- 关键公式：奖励函数 `R_t`、PPO-clip 目标、STTA 损失函数等（详见论文 4.1-4.2节）。

## 3. 实验设计
### 数据集/场景
- 使用**五个真实图数据集**覆盖不同领域：
  - 金融网络（Elliptic，203,769节点）
  - 化学分子（QM9，约18节点/图）
  - 社交网络（Facebook + Twitter，最大81,306节点）
  - 引文网络（Cora、CiteSeer、PubMed，最大19,717节点）
  - 交通网络（METR-LA，207节点）
- 构建了 **SFT 数据集**（9,986个（查询、工具序列、答案）三元组）和 **RL 数据**（3,000个专家标注的（查询、答案）对），每个场景 500 训练/100 测试。

### 基准方法
- **文本指令方法**：Claude系列、GPT系列、GLM4、NLGraph、GraphWiz。
- **工具指令方法**：Graph-ToolFormer、GraphForge、ToolGen。
- 为确保公平，基线使用的图被限制为子图（<100节点），而 GraphChain 可处理高达20万节点的全图。

## 4. 资源与算力
- **训练算力**：使用了 2 张 NVIDIA A800 (80GB) GPU。
- **训练方式**：基于 Qwen2.5-7B-instruction 模型，采用 LoRA 微调（rank=16, alpha=32）。
- **训练阶段**：SFT（8 epoch，学习率5e-5）、RL（PPO，学习率1e-5）、STTA（学习率0.01）。
- 论文未报告总训练时长，但硬件配置明确。

## 5. 实验数量与充分性
- **主要实验**：在 5 个数据集上对比了 11 种基线，报告了平均准确率及标准差（两个样本 t 检验 p<0.05 证实显著性）。
- **消融实验**：两个变体（去除渐进图蒸馏、去除 STTA），展示了两个组件的各自贡献。
- **可扩展性分析**：在图大小（50-200k节点）和查询复杂度（1-5工具步骤）两个维度上比较了 GPT-4、GraphForge 和 GraphChain。
- **迁移学习评估**：仅在金融网络上训练，测试其他三个领域，并对比有/无 STTA 的效果。
- **工具链分析**：按功能聚类工具（图统计、子图提取、路径规划等），展示不同领域的工具使用分布。
- **鲁棒性研究**：使用不同基座模型（Qwen2.5、Llama3.1、GLM4）以及不同模型规模（3B、7B、14B）验证一致性；还测试了缩减工具库（移除50%）时的性能保持。
- **总计超过10组实验**，覆盖主流场景与分析方法，实验设计较为全面、公平。

## 6. 论文的主要结论与发现
- GraphChain **平均准确率 84.7%**，比最强基线 GraphForge（70.2%）**提升 20.7%**，且参数量仅 7B（远小于 GPT-4o 的 200B）。
- 渐进图蒸馏和 STTA 两个组件均不可或缺，去除任一部分性能显著下降，且蒸馏组件更为关键。
- 在图规模高达 20 万节点时，GraphChain 仍保持 ~79.5% 准确率，而基线在更大图时急剧下降。
- 跨领域迁移能力强，STTA 有效降低性能衰减（降幅从 8-10% 缩至 3-5%）。
- 工具使用模式因领域而异（如交通网络偏向路径规划，社交网络偏向中心度和社区检测），表明模型习得了自适应策略。
- 在不同基座模型上表现一致，鲁棒性良好。

## 7. 优点
- **方法创新**：将图分析建模为动态工具链，结合强化学习中的信息瓶颈思想（渐进图蒸馏），理论上有证明，实践中有效。
- **可扩展性**：通过工具输出摘要而非全图描述，克服 LLM 上下文限制，能处理十万级节点图。
- **自适应高效**：STTA 仅需轻量适配器，避免重训练，利用谱特征巧妙捕捉全局结构。
- **实验扎实**：覆盖多领域、多种基线、多个维度（消融、可扩展、迁移、工具分析、鲁棒性），统计显著性明确，可复现（代码已开源）。

## 8. 不足与局限
- **静态图假设**：当前实现主要针对静态图，未涉及动态/时序图（如社交网络随时间变化），需要进一步扩展。
- **工具库依赖**：虽然使用了 45 个 NetworkX 函数，但仍可能不够覆盖某些专业领域（如生物信息、复杂网络动力学），扩展性待验证。
- **训练数据构建成本**：SFT 和 RL 数据集依赖 GPT-4 生成和人工标注（3,000 对专家标注），在小样本或新领域可能难以复现。
- **评估上的潜在偏差**：基线方法被限制在子图（<100节点），而 GraphChain 在全图上运行，虽然体现了优势，但比较条件不完全对称；另外，某些基线（如 GPT-4o）可能因 prompt 设计而表现不佳，存在对基线调优不充分的风险。
- **理论证明的局限性**：命题 4.1 的证明依赖于一些强假设（如相关性正比于互信息、GDL 正比于复杂度的线性近似），实际中未必严格成立。

（完）
