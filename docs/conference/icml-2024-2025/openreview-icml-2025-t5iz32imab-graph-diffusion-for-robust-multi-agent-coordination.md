---
title: Graph Diffusion for Robust Multi-Agent Coordination
title_zh: 面向鲁棒多智能体协作的图扩散方法
authors: "Xianghua Zeng, Hang Su, Zhengyi Wang, Zhiyuan LIN"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=T5IZ32ImAB"
tags: ["query:graph-part"]
score: 8.0
evidence: 基于图扩散的多智能体并行决策与协作
tldr: 离线多智能体强化学习面临分布外状态估计挑战。本文提出MCGD框架，基于图扩散模型构建稀疏协调图，融合连续节点和离散边属性，以增强协作策略的鲁棒性。实验表明MCGD在动态环境中优于现有方法，有效提升了多智能体并行决策的稳定性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 703, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 726, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1776, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-t5iz32imab/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 844, \"height\": 633, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1775, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1792, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 859, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 801, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 657, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 776, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1774, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-t5iz32imab/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1777, \"height\": 420, \"label\": \"Table\"}]"
motivation: 现有离线MARL方法忽略多智能体协作动态，导致策略鲁棒性不足。
method: 构建稀疏协调图，利用图扩散模型对节点和边属性进行联合建模，增强协作。
result: 在多个动态环境基准中，MCGD的协作策略鲁棒性显著优于基线。
conclusion: 图扩散能有效提升多智能体离线协作决策的鲁棒性。
---

## Abstract
Offline multi-agent reinforcement learning (MARL) struggles to estimate out-of-distribution states and actions due to the absence of real-time environmental feedback. While diffusion models show promise in addressing these challenges, their application primarily focuses on independently diffusing the historical trajectories of individual agents, neglecting crucial multi-agent coordination dynamics and reducing policy robustness in dynamic environments. In this paper, we propose MCGD, a novel Multi-agent Coordination framework based on Graph Diffusion models to improve the effectiveness and robustness of collaborative policies. Specifically, we begin by constructing a sparse coordination graph that includes continuous node attributes and discrete edge attributes to effectively identify the underlying dynamics of multi-agent interactions. Next, we derive transition probabilities between edge categories and present adaptive categorical diffusion to capture the structure diversity of multi-agent coordination. Leveraging this coordination structure, we define neighbor-dependent forward noise and develop anisotropic diffusion to enhance the action diversity of each agent. Extensive experiments across various multi-agent environments demonstrate that MCGD significantly outperforms existing state-of-the-art baselines in coordination performance and policy robustness in dynamic environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：离线多智能体强化学习（Offline MARL）由于缺乏与环境的实时交互，难以处理训练数据之外的分布外（OOD）状态和动作，导致策略泛化能力差、鲁棒性不足。
- **现有局限**：已有的扩散模型（如MADIFF、DOM2）虽能缓解OOD问题，但仅对每个智能体的历史轨迹进行独立扩散，忽略了智能体之间的协调动态（如协调结构变化）。例如，当某个智能体速度改变或突然失效时，独立扩散方法无法自适应调整协作关系，导致任务失败。
- **本文目标**：提出第一个基于图扩散的离线多智能体协调框架MCGD，通过显式建模智能体间的协调结构（离散边）和个体动作多样性（连续节点），提升协作策略的有效性和鲁棒性。

## 2. 方法论

- **核心思想**：将多智能体系统的状态表示为一个**稀疏协调图**，其中节点为连续动作向量，边为离散的二进制连接（表示是否存在协作关系）。然后设计一个**图扩散过程**，同时处理边（结构）和节点（动作）的演化，包括前向加噪和反向去噪，最终生成鲁棒的协作策略。
- **关键技术细节**：
  - **稀疏协调图构建**：在每个时间步，基于智能体观测的余弦相似度，为每个智能体选取k个最近邻构成k近邻图，作为初始协调图。
  - **分类扩散（Categorical Diffusion）**：用于边的离散属性。利用观测相似度矩阵C，定义自适应转移矩阵 \(Q_t = e^{(C-D)t}\)（D为度矩阵），满足对称性、可加性、局部性和收敛性。前向过程对边类别按概率转移；反向去噪使用贝叶斯公式采样，由图变换网络预测干净边。
  - **异向扩散（Anisotropic Diffusion）**：用于节点的连续动作。对每个智能体，根据其邻居动作计算协方差矩阵Σ_i，从而定义各向异性的高斯噪声。前向过程为 \(q(a_{i,k}|a_{i,k-1}) = \mathcal{N}(\sqrt{1-\beta_k} a_{i,k-1}, \beta_k \Sigma_i)\)，闭式形式使采样高效。
  - **去噪网络**：使用图变换网络（Graph Transformer）同时预测干净边和干净节点。损失函数包括边的交叉熵损失和节点的欧氏距离+Q损失（结合Q函数引导）。
  - **策略采样**：在运行时，每个智能体先通过Q值从候选动作中选优，初始化全连接图，然后迭代去噪得到最终动作。离散动作空间通过softmax+argmax处理。

## 3. 实验设计

- **基准环境与数据集**：
  - **MPE**（粒子环境）：Spread、Tag、World三个任务，使用OMAR提供的离线数据集（Expert、Medium、Medium-Replay、Random）。
  - **MAMuJoCo**：2halfcheetah、2ant、4ant三个配置，使用Off-the-Grid MARL框架生成的数据集（Good、Medium、Poor）。
  - **SMAC**（星际争霸多智能体挑战）：3m、2s3z、5m6m、8m四个地图，同样使用Off-the-Grid数据集（Good、Medium、Poor）。
- **对比方法**：
  - 传统离线MARL：MA-ICQ、MA-CQL、OMAR。
  - 扩散策略基线：MA-SfBC（单智能体扩散扩展）、DOM2、MADIFF（多智能体扩散）。
- **评估指标**：平均episodic return，多次随机种子取均值±标准差。

## 4. 资源与算力

- **文中信息**：
  - 硬件：Linux服务器，64核Intel Xeon Platinum 8336C CPU（2.30 GHz），NVIDIA A800-SXM4-80GB GPU。
  - 超参数：扩散步数K∈[50,200]，学习率2e-4，批大小32，折扣因子0.99，Adam优化器。
- **未明确说明**：具体GPU数量、总训练时长、各实验的耗时。因此无法给出精确的算力投入细节。

## 5. 实验数量与充分性

- **实验组数**：非常充分。
  - **表1**：在3个基准的10个任务上对比Expert/Good数据集，共10组。
  - **表2**：在4个任务上针对两种动态变化（属性变化、结构变化）的shifted环境，共4×2=8组。
  - **表3**：SMAC上对比邻居观测处理方式（平均vs拼接），4个地图。
  - **图6**：消融分类扩散和异向扩散两个模块，在SMAC的3个难度级别上，共4×3=12组。
  - **附录表7-9**：在MPE、MAMuJoCo、SMAC的更多难度（Random、Medium-Replay、Poor等）上补充实验，覆盖所有数据集质量。
  - **图7**：敏感性分析（λ系数）在Tag任务的4个难度上。
  - **表6**：采样效率（不同智能体数量）。
- **充分性与公平性**：
  - 覆盖了多种环境、多个数据质量级别，评估了鲁棒性（shifted环境），并进行了消融研究。
  - 所有基线使用相同的公共数据集和官方实现，设置一致。
  - 多次随机种子运行，报告均值与标准差，统计可靠性较高。
- **结论**：实验设计合理、全面，结果客观可靠。

## 6. 主要结论与发现

- **性能优势**：MCGD在所有基准上均显著优于现有SOTA，在Expert/Good数据集上提升幅度为5.0%～12.8%，在动态shifted环境中提升最高达14.2%。
- **鲁棒性**：在智能体属性变化（如速度降低）或结构变化（如智能体突然失效）时，MCGD能自适应调整协作策略，保持高回报，而基线方法性能大幅下降。
- **关键模块有效性**：消融实验表明，同时保留分类扩散（建模结构多样性）和异向扩散（建模动作多样性）是性能最佳的关键。固定协调结构（MCGD-CD）或独立扩散（MCGD-AD）均导致显著下降。
- **效率可接受**：MCGD的采样时间略高于MADIFF，但随智能体数量增长保持稳定说明具有良好的可扩展性。

## 7. 优点

1. **创新性**：首次将图扩散模型引入离线多智能体强化学习，同时建模边（结构）和节点（动作）的扩散过程。
2. **方法设计合理**：分类扩散利用观测相似度自适应定义转移矩阵，满足理论属性（对称、可加、收敛）；异向扩散通过邻居动作协方差实现各向异性加噪，使动作多样性依赖于协调结构。
3. **实验全面**：涵盖多种环境、多个数据质量级别，特别设计了动态shifted环境评估鲁棒性，消融实验验证了每个组件的贡献。
4. **可视化分析**：展示了协调图在任务执行中的动态演化，说明了模型能自适应调整协作关系（如失效智能体被孤立）。
5. **开源可复现**：提供了详细实现细节和算法伪代码（Algorithm 1, 2），便于复现。

## 8. 不足与局限

1. **真实应用验证缺失**：所有实验均在仿真环境中进行，未在真实机器人或物理系统上测试，实际部署效果未知（作者承认正在推进，但尚未有结果）。
2. **图构建简化**：基于k近邻和观测相似度构建协调图，可能无法捕捉更复杂的任务依赖关系（如时序依赖、非对称关系），作者也指出未来需引入更复杂的图结构。
3. **算力资源报告不完整**：未提供训练总耗时、GPU数量等具体信息，难以评估方法的计算成本。
4. **基线略有限制**：部分基线（如MA-TD6、QMIX）用于生成数据集，但对比方法中未包含最新的基于Transformer的离线MARL方法，可能存在对比不够全面的风险。
5. **采样效率略有开销**：尽管可接受，但MCGD的采样时间比MADIFF稍高，在实时性要求极高的场景中可能需要优化。

（完）
