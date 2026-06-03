---
title: Mastering Massive Multi-Task Reinforcement Learning via Mixture-of-Expert Decision Transformer
title_zh: 通过混合专家决策Transformer掌握大规模多任务强化学习
authors: "Yilun Kong, Guozheng Ma, Qi Zhao, Haoyu Wang, Li Shen, Xueqian Wang, Dacheng Tao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qUcUyqP1UA"
tags: ["query:graph-part"]
score: 9.0
evidence: 混合专家决策Transformer用于多任务强化学习
tldr: 离线多任务强化学习在任务数量极大时性能下降。本文提出M3DT框架，通过混合专家架构扩展模型参数，有效缓解了任务增多带来的退化，在数百个任务上展现出卓越的可扩展性和性能，为大规模多任务RL提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 801, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 846, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1678, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 838, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 849, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 841, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 839, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1569, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 744, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 750, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qucuyqp1ua/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1764, \"height\": 1334, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1768, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1076, \"height\": 1394, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 937, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 793, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1414, \"height\": 538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qucuyqp1ua/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1415, \"height\": 537, \"label\": \"Table\"}]"
motivation: 现有MTRL方法在任务数量极大时性能下降。
method: 提出M3DT，基于混合专家架构增强参数可扩展性。
result: 在大量任务上性能显著提升，可扩展性强。
conclusion: M3DT证明了参数扩展对大规模MTRL的有效性。
---

## Abstract
Despite recent advancements in offline multi-task reinforcement learning (MTRL) have harnessed the powerful capabilities of the Transformer architecture, most approaches focus on a limited number of tasks, with scaling to extremely massive tasks remaining a formidable challenge. In this paper,  we first revisit the key impact of task numbers on current MTRL method, and further reveal that naively expanding the parameters proves insufficient to counteract the performance degradation as the number of tasks escalates. Building upon these insights, we propose M3DT, a novel mixture-of-experts (MoE) framework that tackles task scalability by further unlocking the model’s parameter scalability.  Specifically, we enhance both the architecture and the optimization of the agent, where we strengthen the Decision Transformer (DT) backbone with MoE to reduce task load on parameter subsets, and introduce a three-stage training mechanism to facilitate efficient training with optimal performance. Experimental results show that, by increasing the number of experts, M3DT not only consistently enhances its performance as model expansion on the fixed task numbers, but also exhibits remarkable task scalability, successfully extending to 160 tasks with superior performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 一、论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现有离线多任务强化学习（MTRL）方法大多聚焦于有限数量的任务（如几十个），当任务数量扩展到极大（如数百个）时，性能显著下降。同时，简单地扩大模型参数（如增加Transformer宽度）很快达到性能天花板，无法有效缓解任务数量增加带来的退化。
- **核心问题**：如何同时实现任务可扩展性（task scalability）和参数可扩展性（parameter scalability），使模型能高效处理海量任务。
- **整体含义**：本文提出M3DT（Mixture-of-Expert Decision Transformer），通过混合专家（MoE）架构增强参数可扩展性，从而解决大规模多任务RL中的性能退化问题，证明了通过合理扩大参数数量可反向促进任务可扩展性。

## 二、论文提出的方法论

### 核心思想
- 通过任务分组和参数分离，将每个专家（expert）分配给一个小型任务子集，大幅降低每个参数子集上的学习负担。
- 通过增加专家数量，既能扩大模型参数量，又能进一步减少每个专家需处理的任务数，形成相互增强的循环。

### 关键技术细节
1. **架构设计**（在Decision Transformer上集成MoE）：
   - 保留Prompt-DT的完整骨干网络（含FFN），在每个Transformer block的FFN旁并行添加多个专家模块（结构与FFN相同）和一个路由器（Router，MLP）。
   - 前向传播时：`f(x) = x + f_FFN(x) + f_MoE(x)`，其中 `f_MoE(x) = ∑ Softmax(f_router(x))_i · f_expert_i(x)`。
   - 骨干网络学习所有任务的共享知识，每个专家专门学习其对应的小型任务子集的特定知识。

2. **三阶段训练机制**（Three-Stage Training）：
   - **阶段1：骨干训练（Backbone Training）**：用全部任务训练Prompt-DT，但只在梯度冲突达到峰值前进行早期停止（约400k步），避免过度拟合主导任务。
   - **阶段2：任务分组与专家独立训练（Task Grouping & Expert Training）**：先将所有任务分组（两种策略：随机分组或基于梯度相似性的K-means分组），然后冻结骨干，每个专家在其对应的任务子集上独立训练。
   - **阶段3：路由器训练（Router Training）**：冻结骨干和所有专家，仅训练路由器，使其能根据骨干隐藏状态动态分配各专家的权重，实现无需任务ID的统一策略。

## 三、实验设计

### 数据集/场景
- **160个连续控制任务**，来自三个域：
  - Meta-World（50个操作任务，Sawyer机器人）
  - DMControl（30个控制任务，包括19个原始任务+11个自定义任务）
  - MuJoCo Locomotion（80个任务：Cheetah-vel 40个 + Ant-dir 40个）
- 状态和动作空间不一致时，采用零填充至最大维度（39维状态，8维动作），并对无效动作维度进行掩码。
- 评估指标：各任务归一化分数（success rate或线性映射后的分数）的平均值。

### Benchmark与对比方法
- 基线方法：MTDT（带任务ID编码的DT）、PromptDT（轨迹提示DT）、HarmoDT（和谐掩码多任务DT）。
- 每个基线均比较其默认小尺寸（1.47M参数）和大尺寸（173.30M参数）。
- M3DT变体：M3DT-Random（随机分组）、M3DT-Gradient（基于梯度分组）。

### 实验设置
- 任务选择：控制平均任务难度一致，保持域比例（MW:DMC:Ant:Cheetah=5:3:4:4），对不同种子使用不同任务组合。
- 消融实验：包括是否使用三阶段训练、是否分组、是否冻结专家等。
- 参数可扩展性实验：在80和160任务下增加专家数量（8~48个）。
- 不同骨干训练停止步数的影响分析。

## 四、资源与算力

论文在附录A.6和B.4中明确说明了：
- **GPU型号**：NVIDIA GeForce RTX 4090（HarmoDT-Large使用NVIDIA A100 40G）。
- **训练时长**（以M3DT-5M骨干为例）：
  - 阶段1（骨干训练 40万步）：约5.2小时。
  - 阶段2（专家独立训练，并行执行一个专家）：约1.8小时。
  - 阶段3（路由器训练 40万步）：约17.2小时（因代码未并行化，可优化）。
  - 总计约24.2小时。
- 对比：PromptDT-173M和MTDT-173M约21.3小时，HarmoDT-173M约95.6小时。
- 所有实验使用3个随机种子。

## 五、实验数量与充分性

- **实验数量**：非常充分。
  - 在10、20、40、80、120、160任务规模下均进行了对比。
  - 表1展示了主要结果，图3展示了参数扩展热力图，图6展示了专家数扩展曲线。
  - 消融实验（表2）对比了是否使用三阶段训练、是否分组、是否冻结专家等。
  - 额外分析包括：骨干训练步数影响（图7）、路由器设计（Top-K vs 全连接，图9）、模块级梯度冲突分析（图12）、领域分解结果（附录B表6-7）。
- **公平性**：
  - 任务选择平衡了难度、域比例和多样性。
  - 基线均使用了相同参数规模的变体。
  - 多次重复（3种子）并报告均值和标准差。
- **充分性**：实验覆盖了任务可扩展性、参数可扩展性、消融分析、分组策略对比，结论有充分数据支撑。

## 六、论文的主要结论与发现

1. **任务数量增加导致性能下降，且梯度冲突加剧**：当任务数从10增至160时，模型性能持续下降，但下降趋势在任务数超过80后变缓。
2. **简单扩大模型参数效果有限**：在MTRL中，模型参数超过20M后进一步扩大不再带来性能提升，与LLM中的缩放定律不同。
3. **M3DT通过MoE与三阶段训练有效实现任务和参数可扩展性**：
   - 在固定任务数下增加专家数可稳定提升性能。
   - 在160任务下，M3DT-Gradient达到78.21分，远超最好基线（HarmoDT-Large 72.80分，提升7.5%）。
4. **分组策略的影响**：基于梯度的分组优于随机分组，但即便随机分组也大幅超越基线。
5. **三阶段训练至关重要**：端到端训练或跳过分组训练均导致性能大幅下降。
6. **路由器设计**：全连接软路由比Top-K稀疏路由更适合该框架，Top-K路由难以随专家数扩展。

## 七、优点

- **问题洞察深刻**：通过大量实验揭示了MTRL中任务数量与模型缩放的瓶颈，提出“减少每个参数子集的任务数”这一关键思路。
- **方法新颖**：将MoE与DT结合，并设计了三阶段训练机制，避免了传统MoE训练中的负载不均衡和梯度冲突问题。
- **实验设计严谨**：包括任务难度控制、域比例保持、多消融、参数扩展分析等，确保了结论的可靠性。
- **可扩展性强**：通过增加专家数量即可同时提升参数和任务可扩展性，为大规模MTRL提供了新范式。
- **透明性**：详细报告了算力消耗、训练步骤和超参数，有利于复现。

## 八、不足与局限

- **网络架构未深入优化**：专家和路由器的设计较为简单（FFN结构、MLP路由器），未探索更高效的模块化设计，可能导致参数利用率不够高。
- **缺乏泛化和持续学习能力**：论文未涉及对未见过任务的泛化或增量任务学习，虽然指出模块化特性自然支持，但未实验验证。
- **推理成本随专家数上升**：全连接软路由需计算所有专家，激活所有专家权重；尝试Top-K路由会降低性能，实际部署时可能成本过高。
- **性能天花板**：专家数量超过40后增益明显减小（图6），骨干容量和共享知识有限可能是瓶颈。
- **环境多样性有限**：虽然用了160个任务，但均为连续控制任务，未涉及离散动作或图像输入等更复杂的场景，泛化性有待验证。

（完）
