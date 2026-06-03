---
title: "HYGMA: Hypergraph Coordination Networks with Dynamic Grouping for Multi-Agent Reinforcement Learning"
title_zh: HYGMA：用于多智能体强化学习的动态分组超图协调网络
authors: "Chiqiang Liu, Dazi Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=mgJkeqc685"
tags: ["query:graph-part"]
score: 9.0
evidence: 基于超图协调网络的动态分组多智能体强化学习
tldr: 该论文针对合作多智能体强化学习中的协调挑战，提出HYGMA框架。它利用动态谱聚类对智能体状态历史进行分组，构建超图结构以捕获高阶关系，并利用注意力机制增强信息传递。实验表明，在需要自适应协调的任务中，HYGMA大幅提升了学习效率和团队奖励。该方法促进了多智能体系统中的动态协作模式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-mgjkeqc685/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-mgjkeqc685/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1763, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-mgjkeqc685/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1772, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-mgjkeqc685/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-mgjkeqc685/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 847, \"height\": 428, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 1497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 817, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 978, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 911, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 902, \"height\": 617, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1207, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-mgjkeqc685/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 963, \"height\": 199, \"label\": \"Table\"}]"
motivation: 多智能体系统中智能体间的协调模式需要动态适应，而现有方法缺乏灵活的群体形成机制。
method: 结合动态谱聚类和超图神经网络，自适应地构建智能体分组并在超图上进行信息聚合。
result: 在多个合作任务上，HYGMA比现有方法更快收敛并取得更高累积奖励。
conclusion: 为多智能体动态协调提供了一种有效的超图框架，推动了自适应群体智能的发展。
---

## Abstract
Cooperative multi-agent reinforcement learning faces significant challenges in effectively organizing agent relationships and facilitating information exchange, particularly when agents need to adapt their coordination patterns dynamically. This paper presents a novel framework that integrates dynamic spectral clustering with hypergraph neural networks to enable adaptive group formation and efficient information processing in multi-agent systems. The proposed framework dynamically constructs and updates hypergraph structures through spectral clustering on agents' state histories, enabling higher-order relationships to emerge naturally from agent interactions. The hypergraph structure is enhanced with attention mechanisms for selective information processing, providing an expressive and efficient way to model complex agent relationships. This architecture can be implemented in both value-based and policy-based paradigms through a unified objective combining task performance with structural regularization. Extensive experiments on challenging cooperative tasks demonstrate that our method significantly outperforms state-of-the-art approaches in both sample efficiency and final performance. The code is available at: https://github.com/mysteryelder/HYGMA.

---

## 论文详细总结（自动生成）

# HYGMA 论文总结

## 1. 核心问题与整体含义（研究动机与背景）
合作式多智能体强化学习（MARL）面临的关键挑战是如何高效地组织智能体之间的关系并促进信息交换。现有方法（如值分解、固定通信结构）只能建模成对交互或依赖静态分组，无法适应任务中动态变化的协调需求。论文旨在通过**动态分组**与**高阶关系建模**来解决这一瓶颈，提升协同效率与学习性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将动态谱聚类与超图神经网络（HGCN）结合，使智能体间的分组能随状态历史自适应演化，并利用超图自然捕获多智能体间的高阶交互。
- **关键技术细节**：
  - 动态谱聚类：基于智能体的状态历史矩阵计算相似性图，通过归一化割的谱松弛求解分组。组数由剪影系数自动优化。分组更新由稳定性阈值 δ 控制，保证收敛。
  - 超图构建与注意力增强：每组对应一条超边，超边权重由组内凝聚度（剪影分数）定义。采用多头注意力机制对超边信息进行选择性聚合，生成组感知的智能体表示。
  - 统一学习目标：\( \mathcal{L}_{total} = \mathcal{L}_{task} + \lambda_1 \mathcal{L}_{group} + \lambda_2 \mathcal{L}_{att} \)，其中组一致性损失鼓励组内紧致、组间分离，注意力熵正则化避免平凡解。
  - 双范式实现：分别基于 QMIX（值函数）和 Actor‑Critic（策略梯度）进行集成，均遵循 CTDE 原则。

## 3. 实验设计
- **数据集/场景**：
  - SMAC（星际争霸II微操）：3s_vs_5z（Hard）、5m_vs_6m（Hard）、3s5z_vs_3s6z（Super Hard）
  - Predator‑Prey：中规模（10×10网格，5个捕食者）与大规模（20×20，10个捕食者）
  - Traffic Junction：7×7（最多5辆车）与14×14（最多10辆车）
  - Google Research Football（GRF）：3名攻击者对抗内置AI
- **对比方法**：
  - SMAC：Ft‑QMIX、QPLEX、VAST、MAPPO、GoMARL、RIIT
  - Predator‑Prey / Traffic Junction / GRF：MAGIC、CommNet、GA‑Comm、I3CNet、TarMAC‑IC3Net
- **评价指标**：胜率、收敛步数、平均步数、成功率

## 4. 资源与算力
论文**未明确说明**使用的 GPU 型号、数量或训练时长。仅提供了 HGCN 模块的额外参数量和约 36% 的训练时间开销，并指出该开销被显著的样本效率提升所补偿。

## 5. 实验数量与充分性
- **实验数量**：覆盖 4 个环境共 8 个不同规模的场景；与 10 余种基线方法对比；包含完整的消融实验（替换超图为普通 GCN、固定单组）以及分组结构可视化分析（共现矩阵）。
- **充分性与客观性**：实验设计全面，基准覆盖广泛，消融验证了各组件的必要性。结果报告包含均值和标准差，统计上可靠。但缺少对**超大规模智能体（如 >50）** 的测试，以及开放竞争场景（如混合合作-竞争）的验证。

## 6. 主要结论与发现
- HYGMA 在样本效率和最终性能上**显著优于所有基线方法**，尤其是在需要复杂协调的任务（如 SMAC 3s5z_vs_3s6z、大规 Predator‑Prey）中优势明显。
- 动态谱聚类能够自动发现可解释的战术角色（如核心小组、灵活支援、独立单元），且分组结构在学习后期收敛稳定。
- 超图结构比普通图结构（GCN）和静态单组结构更具表达能力，是性能提升的关键。
- 理论分析证明了分组近似比、收敛性以及值函数损失上界，支撑了方法的有效性。

## 7. 优点
- **方法创新性强**：首次将动态谱聚类与超图神经网络结合，自适应捕获高阶协调模式，突破了传统图网络的成对局限。
- **理论保障充分**：提供了聚类近似、收敛性和质量保持的严格定理，增强了方法可信度。
- **统一双范式**：同时兼容值函数与策略梯度框架，扩展性强。
- **实验全面公正**：覆盖多领域基准，消融分析清晰，分组可视化提供了可解释性。

## 8. 不足与局限
- **计算开销**：HGCN 引入约 36% 的训练时间增加，尽管被效率提升补偿，但在资源受限场景下仍可能成为瓶颈。
- **规模局限性**：未在超过 20 个智能体的场景中测试，大规模可扩展性有待验证。
- **分组稳定性受噪声影响**：谱聚类依赖状态历史，当观测噪声较大时可能影响分组质量，论文未讨论鲁棒性。
- **超参数敏感度**：λ₁、λ₂、δ 等超参数需手工设定，虽提供了默认值，但缺乏系统的敏感度分析。
- **缺乏开放竞争环境验证**：仅评估了完全合作任务，在混合动机或对抗性环境中的表现未知。

（完）
