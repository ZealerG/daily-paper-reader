---
title: "PARCO: Parallel AutoRegressive Models for Multi-Agent Combinatorial Optimization"
title_zh: PARCO：用于多智能体组合优化的并行自回归模型
authors: "Federico Berto, Chuanbo Hua, Laurin Luttmann, Jiwoo Son, Junyoung Park, Kyuree Ahn, Changhyun Kwon, Lin Xie, Jinkyoo Park"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=9F2Cmgo17M"
tags: ["query:graph-part"]
score: 9.0
evidence: 并行自回归强化学习用于多智能体组合优化
tldr: 本文针对多智能体组合优化问题中协调差、泛化弱和延迟高的挑战，提出PARCO框架。该框架集成基于Transformer的通信层实现智能体并行协作，采用并行自回归解码加速求解。实验表明PARCO在多种多智能体组合任务上显著优于现有方法，提升了解决方案质量和计算效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 656, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 468, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 643, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 734, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9f2cmgo17m/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1321, \"height\": 1489, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 1327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 514, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1094, \"height\": 508, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1235, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1311, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9f2cmgo17m/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1438, \"height\": 337, \"label\": \"Table\"}]"
motivation: 多智能体组合优化NP难且需要有效协调，现有学习模型协调差、泛化弱、延迟高。
method: 提出通用RL框架PARCO：集成Transformer通信层实现智能体并行协作，采用并行自回归解码快速构建高质量解。
result: 在多种多智能体组合任务上，PARCO相比基线显著提升解质量和效率。
conclusion: PARCO为多智能体组合优化提供了一种高效且可扩展的RL方案。
---

## Abstract
Combinatorial optimization problems involving multiple agents are notoriously challenging due to their NP-hard nature and the necessity for effective agent coordination. Despite advancements in learning-based methods, existing approaches often face critical limitations, including suboptimal agent coordination, poor generalization, and high computational latency. To address these issues, we propose PARCO (Parallel AutoRegressive Combinatorial Optimization), a general reinforcement learning framework designed to construct high-quality solutions for multi-agent combinatorial tasks efficiently. To this end, PARCO integrates three key novel components: (1) transformer-based communication layers to enable effective agent collaboration during parallel solution construction, (2) a multiple pointer mechanism for low-latency, parallel agent decision-making, and (3) priority-based conflict handlers to resolve decision conflicts via learned priorities. We evaluate PARCO in multi-agent vehicle routing and scheduling problems, where our approach outperforms state-of-the-art learning methods, demonstrating strong generalization ability and remarkable computational efficiency. We make our source code publicly available to foster future research: https://github.com/ai4co/parco.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：多智能体组合优化（Multi-Agent CO）问题（如多车辆路径规划、柔性流水车间调度）具有NP难性质，且需要多个异构智能体有效协调，实际应用中非常困难。
- **现有方法局限**：传统精确/启发式方法耗时长；现有基于学习的自回归（AR）模型存在智能体协调差、泛化能力弱、计算延迟高三大瓶颈。
- **目标**：提出PARCO框架，通过**并行自回归**构造解，兼顾解质量、泛化性和效率。

## 2. 方法论
- **核心思想**：将多智能体CO建模为**并行多智能体MDP**，在每个构造步骤同时为所有智能体生成动作，显著减少总步数（从所有智能体步数之和降为最大步数）。
- **关键技术细节**：
  - **多智能体编码器**：分别嵌入智能体特征和节点特征，通过自注意力或交叉注意力交互。
  - **通信层（Communication Layers）**：在解码每一步，通过Transformer多头自注意力和MLP处理智能体查询向量，实现智能体间的状态共享与协调。
  - **多指针机制（Multiple Pointer Mechanism）**：一个解码器同时输出所有智能体对节点的联合概率分布，通过mask保证可行性。
  - **基于优先级的冲突处理器**：当多个智能体选择同一节点时，根据模型输出的概率（或启发式）决定优先级，优先级高的执行动作，其余执行回退（保持原地），并利用向量化算法高效实现。
  - **训练方式**：使用REINFORCE + 共享基线（SymNCO的多重对称性增强），目标函数为奖励（负成本）最大化。

## 3. 实验设计
- **数据集/场景**：三类问题
  - **min-max HCVRP**（异构容量车辆路径）：N=60/100，M=3/5/7，节点和需求随机生成。
  - **OMDCPDP**（开放多仓库取送货）：N=50/100，M=5/7/10/10/15/20，并做了大规模泛化测试（N=500/1000，M=50~200及5000规模）。
  - **FFSP**（柔性流水车间调度）：N=20/50/100，M=12/18/24/30，处理时间随机。
- **基准方法**：传统求解器（SISR、OR-Tools、Gurobi、GA、SA、PSO等）和神经基线（AM、ET、DPN、2D-Ptr、DRL Li、HAM、MAPDP、MatNet等）。
- **评价指标**：目标值（Obj.）、与最优解间隙（Gap）、单实例推断时间（Time）。报告贪心（g.）和采样（s.）结果。

## 4. 资源与算力
- **硬件**：2×Intel Xeon Gold 6338 CPU，8×NVIDIA RTX 4090（24GB VRAM）。
- **软件**：Python 3.12, PyTorch 2.5, PyTorch Lightning, RL4CO库。
- **训练时长**：均小于24小时。具体：HCVRP约15小时（4 GPU, batch 512），OMDCPDP小于5小时（1 GPU, batch 128），FFSP单独训练各规模模型（100~200 epochs）。

## 5. 实验数量与充分性
- **主实验**：三个问题共约20种（N, M）组合，每种都对比多个基线并报告结果。
- **消融实验**：通信层效果（无/MLP/MHA/全通信层）、冲突处理器效果（随机/最小/最近/学习优先级），均展示了性能差异。
- **泛化实验**：OMDCPDP上零样本泛化到10倍规模（N=500/1000, M=50~200），以及5000节点XXL测试。
- **速度对比**：PARCO与AR模型在不同M下的推断时间对比，显示加速3.3×~24.7×。
- **收敛分析**：附录C.3给出了不同训练阶段的目标值和标准差，表明训练稳定。
- **充分性**：实验覆盖了不同问题类型、不同规模、多基线对比、关键组件消融、泛化和效率，较为全面。但主表未给出多次运行的误差棒（行业惯例为一次评估平均值），附录提供了收敛标准差。

## 6. 主要结论与发现
- PARCO在所有三个问题、所有配置上**全方位优于现有神经基线**，在解质量（更小目标值或间隙）和推理速度上均有显著提升。
- **通信层**显著提升协调能力和解质量；**学习优先级冲突处理器**优于随机或启发式方法。
- **泛化能力极强**：训练时未见过的N和M（甚至10倍、50倍规模）仍能很好适应，且性能远超OR-Tools。
- **推断时间随智能体数量增加而减少**：并行解码优势，高M场景加速比更大。

## 7. 优点
- **创新性**：首次将并行自回归模式系统引入多智能体CO，通过通信层和多指针机制实现真正的并行协调。
- **通用性**：框架不限定特定问题，可适用于路由和调度等多类多智能体CO。
- **效率**：大幅降低构造步骤，推理延迟低，适合实时应用。
- **泛化能力**：零样本泛化到大规模，无需重新训练。
- **开源**：代码公开，可复现，促进未来研究。

## 8. 不足与局限
- **应用限制**：当前要求已知智能体数量M，无法直接处理M不固定的问题。未来可通过滚动或预测模块扩展。
- **实验覆盖**：仅验证了三种问题（HCVRP、OMDCPDP、FFSP），更多多智能体CO（如多机器人任务分配等）未纳入。
- **偏差风险**：训练数据均为随机生成（均匀分布），真实世界分布可能有偏移，泛化性需要更多验证。
- **训练策略**：FFSP需为每种规模单独训练模型，而HCVRP和OMDCPDP则训练单模型覆盖多种规模，一致性不足。
- **统计严谨性**：主实验结果未公开多次运行的置信区间或标准差，附录仅给出收敛数据，可能削弱结果稳定性判断。

（完）
