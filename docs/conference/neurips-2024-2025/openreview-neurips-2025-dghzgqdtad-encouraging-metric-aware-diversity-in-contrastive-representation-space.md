---
title: Encouraging metric-aware diversity in contrastive representation space
title_zh: 在对比表示空间中鼓励度量感知的多样性
authors: "Tianxu Li, Kun Zhu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DghZGQDTaD"
tags: ["query:graph-part"]
score: 8.0
evidence: 多智能体强化学习中的并行决策多样性促进
tldr: 提出沃瑟斯坦对比多样性探索方法，通过最大化智能体轨迹分布在潜在表示空间中的沃瑟斯坦距离，促进多智能体策略多样性，解决共享参数导致的策略趋同问题。该方法直接针对并行决策场景，提升合作探索效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1074, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1189, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1185, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1288, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1337, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 900, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1286, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dghzgqdtad/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1293, \"height\": 293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 567, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 949, \"height\": 128, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1250, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1351, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 653, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1058, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1459, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 950, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dghzgqdtad/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 418, \"label\": \"Table\"}]"
motivation: 共享网络参数的合作多智能体强化学习中，智能体行为趋同导致探索不足和次优协作策略。
method: 提出沃瑟斯坦对比多样性探索，通过最大化不同智能体轨迹分布的沃瑟斯坦距离来提升策略多样性。
result: 实验表明该方法有效增加策略多样性，提升合作性能。
conclusion: WCD是一种有效的多智能体探索方法，适用于并行决策场景。
---

## Abstract
In cooperative Multi-Agent Reinforcement Learning (MARL), agents that share policy network parameters often learn similar behaviors, which hinders effective exploration and can lead to suboptimal cooperative policies. Recent advances have attempted to promote multi-agent diversity by leveraging the Wasserstein distance to increase policy differences. However, these methods cannot effectively encourage diverse policies due to ineffective Wasserstein distance caused by the policy similarity. To address this limitation, we propose Wasserstein Contrastive Diversity (WCD) exploration, a novel approach that promotes multi-agent diversity by maximizing the Wasserstein distance between the trajectory distributions of different agents in a latent representation space. To make the Wasserstein distance meaningful, we propose a novel next-step prediction method based on Contrastive Predictive Coding (CPC) to learn distinguishable trajectory representations. Additionally, we introduce an optimized kernel-based method to compute the Wasserstein distance more efficiently. Since the Wasserstein distance is inherently defined for two distributions, we extend it to support multiple agents, enabling diverse policy learning. Empirical evaluations across a variety of challenging multi-agent tasks demonstrate that WCD outperforms existing state-of-the-art methods, delivering superior performance and enhanced exploration.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题背景**：在合作多智能体强化学习（MARL）中，参数共享（parameter sharing）能显著降低计算开销并加速训练，但同时导致不同智能体的策略趋于同质化（homogeneous behaviors），进而阻碍有效探索，难以在复杂任务中学习到最优协作策略。
- **现有方法不足**：先前基于互信息（mutual information，如KL散度）的多样性方法仅要求轨迹可区分，无法度量轨迹之间的实际距离，容易因微小差异就达到饱和，探索激励不足；而基于Wasserstein距离的方法（如MAPD、DiCo）虽然天生具有度量感知能力，但在参数共享下初始策略高度相似，导致Wasserstein距离趋近于零，无法提供有效反馈。
- **核心研究目标**：提出一种能产生有效、持续探索激励的多样性促进方法，使Wasserstein距离在对比表示空间中有意义，从而鼓励智能体探索差异更大的轨迹。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **总体思路**：Wasserstein Contrastive Diversity (WCD) —— 在潜在对比轨迹表示空间中最大化不同智能体轨迹分布之间的Wasserstein距离。
- **关键技术细节**：
  1. **可区分轨迹表示学习**：利用对比预测编码（Contrastive Predictive Coding, CPC）进行下一步预测。对每个智能体，编码器 \(g_{\theta_e}\) 将观测-动作对 \(x_t^a = (o_t^a, u_t^a)\) 映射为潜在嵌入 \(z_t^a\)；自回归模型 \(g_{\theta_g}\) 汇总历史嵌入得到轨迹表示 \(c_t^a\)。通过InfoNCE损失（式4）使 \(c_t^a\) 与其对应的下一步嵌入 \(z_{t+1}^a\) 接近，而与其他智能体的嵌入远离，从而学到可区分表示。
  2. **Wasserstein距离计算优化**：采用平滑Wasserstein距离的对偶形式（式5），并使用高斯核函数的随机特征映射（Rahimi & Recht, 2007）参数化对偶函数（\(\mu, \nu\)），只需学习低维对偶向量（维度m=64），避免了端到端神经网络的高计算成本。梯度如式6所示。
  3. **多智能体扩展**：对于超过两个智能体的场景，采用“最近邻Wasserstein距离”作为内在奖励 \(r_w = \min_{a' \neq a} W(p^{\pi_a}, p^{\pi_{a'}})\)，激励每个智能体远离最近的轨迹分布。
  4. **与QMIX集成**：引入额外的内在效用网络 \(Q_w^a\)，独立优化TD损失（式7），与原始QMIX的TD损失加权联合训练（\(L_{total} = L_{TD} + \alpha L_{TD}^w\)，式8），避免直接修改共享团队奖励。
- **算法流程**（伪代码见Appendix C）：采集轨迹 → 训练编码器（最小化InfoNCE） → 训练对偶函数（SGD） → 计算内在奖励 → 联合优化策略网络。

### 3. 实验设计：数据集/场景、基准、对比方法

- **环境**：
  - **Pac‑Men**：4个智能体在迷宫中吃豆子，需要分散到不同房间以最大化收益。
  - **SMAC (StarCraft II)**：6个场景（难度从易到超级难）：3s5z, 2c_vs_64zg, 7sz, 6h_vs_8z, corridor, 3s5z_vs_3s6z（版本SC2.4.10）。
  - **SMACv2**：3个场景（terran_5_vs_5, protoss_5_vs_5, zerg_5_vs_5），引入随机队伍组成和初始位置，增加随机性。
  - **Google Research Football**：3个场景（academy_3_vs_1_with_keeper 等，见附录E.2）。
- **对比方法**：包括价值分解方法（QMIX, QTRAN）、基于角色的（RODE）、基于互信息的（MAVEN, EOI, SCDS, PMIC, LIPO, FoX）、基于Wasserstein距离的（MAPD, DiCo），以及策略梯度方法（MAPPO）。所有方法使用相同网络架构和超参数进行公平比较。
- **评价指标**：平均胜率/平均奖励，报告5个随机种子的均值和标准差。

### 4. 资源与算力

- 文中在Appendix K说明：使用**NVIDIA GeForce RTX 4090 GPU**（未明确数量，推测使用单卡或少量卡）。所有方法运行约5百万步（5M steps）。训练时间对比（Table 9）：在超级难场景corridor上QMIX约7h17m，WCD+QMIX约7h36m；6h_vs_8z上分别约8h35m和8h43m；3s5z_vs_3s6z上约10h42m和10h49m。额外计算开销较小。

### 5. 实验数量与充分性

- **实验组数**：
  - 主对比实验：Pac‑Men、3个SMACv2场景、6个SMAC场景、3个GRF场景，共13个环境，大部分结果以图表（Figure 2,3,4）和汇总表（Table 1,2）展示。
  - 消融实验：在SMAC场景（Figure 6a）中对比了7种变体（去掉自回归、固定编码器、身份预测、生成模型、不同预测目标、不同距离类型等）。
  - 额外分析：不同核函数（Table 6）、内在奖励权重\(\alpha\)（Table 7）、不同代价函数（Table 8）、与\(\epsilon\)-greedy对比（Table 5）、可扩展性（Table 4）、同质行为场景（Table 3）等。
  - 可视化：热力图（图2c-d,图5,8,9）和策略可视化（图7）。
- **充分性与客观性**：报告5个随机种子的均值和标准差，提供标准误差；超参数保持一致（Table 10）；在多个难度级别任务上验证，实验设计覆盖全面、结果可信。消融实验充分论证了各组件的必要性。

### 6. 论文的主要结论与发现

- WCD在所有测试任务上**显著优于**所有对比基线，尤其在SMAC超级难和SMACv2随机环境中提升幅度最大。
- 对比表示学习是使Wasserstein距离有效的关键：固定编码器或使用不太有效的表示学习方法（如预测智能体ID）会导致性能大幅下降。
- 最近邻Wasserstein距离作为内在奖励优于平均随机距离，能更有效地驱动多样性。
- WCD不仅能促进探索，还**不会阻止**智能体在必要时学习同质行为（如集中火力攻击同一敌人），能良好地平衡探索与利用。
- WCD+MAPPO也优于MAPPO，说明方法可推广到策略梯度算法。

### 7. 优点

- **方法创新**：首次将CPC与Wasserstein距离结合解决参数共享下的多样性问题，使度量感知的探索真正有效。
- **计算高效**：采用核方法和对偶向量优化，避免了对每对智能体使用昂贵神经网络，计算开销增加很小（训练时间仅增加约2%-5%）。
- **扩展性好**：通过最近邻内在奖励自然扩展到多智能体场景。
- **理论支撑**：在Appendix B中给出内在奖励有界性的理论证明，为收敛提供了保证。
- **实验全面**：涵盖多个基准、难度、随机种子、消融和可视化，结果可靠。
- **集成灵活**：能与QMIX和MAPPO等主流MARL算法无缝集成。

### 8. 不足与局限

- **代价函数选择**：简化为欧氏距离，但针对特定任务可能存在更优的代价函数（论文第7节指出）。余弦相似度在Pac‑Men中表现更好（Table 8），但未做系统探索。
- **超参数敏感性**：不同场景需要调节内在奖励权重\(\alpha\)和温度参数\(\beta\)（Table 10给出不同值），虽然文中声称不敏感，但仍需手工调整，可能限制实际应用。
- **计算开销**：虽然对比网络增加不大，但WCD比原始QMIX仍需多训练编码器和一对偶向量，对于资源极其受限的环境可能有影响。
- **实验局限性**：主要验证在基于Q学习的方法上，策略梯度方法仅测试了MAPPO，未验证更多其他策略梯度框架（如HAPPO等）。另外，所有实验在离散动作空间进行，连续动作场景未测试。
- **可解释性**：对比表示空间的含义不直观，难以解释为何某些轨迹表示能导致更好的探索。
- **理论深度**：有界性证明较简单，但缺少关于收敛到全局最优或次优界的严格分析。

（完）
