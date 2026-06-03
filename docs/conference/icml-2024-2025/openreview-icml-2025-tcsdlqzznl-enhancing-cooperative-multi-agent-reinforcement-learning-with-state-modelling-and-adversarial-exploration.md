---
title: Enhancing Cooperative Multi-Agent Reinforcement Learning with State Modelling and Adversarial Exploration
title_zh: 通过状态建模和对抗探索增强合作多智能体强化学习
authors: "Andreas Kontogiannis, Konstantinos Papathanasiou, Yi Shen, Giorgos Stamou, Michael M. Zavlanos, George Vouros"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=TCsdlqzZNL"
tags: ["query:graph-part"]
score: 9.0
evidence: 合作多智能体强化学习中的状态建模与对抗探索
tldr: 本文针对分布式部分可观测环境下的合作多智能体强化学习，提出一种状态建模框架，使智能体从局部观测中推断出非观测状态的信念表示，并引入对抗探索策略增强协作。实验结果显示，该方法能有效过滤冗余信息，提升任务完成效率和探索效率，为多智能体系统提供了实用的状态表征方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1482, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1047, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1696, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1258, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 710, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 463, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 485, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 752, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 947, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1470, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1459, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1762, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 734, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1567, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1765, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 580, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 569, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 567, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1728, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 682, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 691, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-tcsdlqzznl/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1457, \"height\": 890, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1687, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 568, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1653, \"height\": 1026, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 532, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 724, \"height\": 1143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 744, \"height\": 1012, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-tcsdlqzznl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 537, \"height\": 795, \"label\": \"Table\"}]"
motivation: 在无通信的分布式部分可观测环境中，多智能体合作面临状态推断和探索困难。
method: 提出状态建模框架，智能体推断非观测状态的信念表示，并结合对抗探索优化策略。
result: 实验表明该方法提升了协作任务执行效果和探索效率。
conclusion: 该研究为多智能体状态表征学习提供了新思路，促进了合作学习性能提升。
---

## Abstract
Learning to cooperate in distributed partially observable environments with no communication abilities poses significant challenges for multi-agent deep reinforcement learning (MARL). This paper addresses key concerns in this domain, focusing on inferring state representations from individual agent observations and leveraging these representations to enhance agents' exploration and collaborative task execution policies. To this end, we propose a novel state modelling framework for cooperative MARL, where agents infer meaningful belief representations of the non-observable state, with respect to optimizing their own policies, while filtering redundant and less informative joint state information. Building upon this framework, we propose the MARL SMPE$^2$ algorithm. In SMPE$^2$, agents enhance their own policy's discriminative abilities under partial observability, explicitly by incorporating their beliefs into the policy network, and implicitly by adopting an adversarial type of exploration policies which encourages agents to discover novel, high-value states while improving the discriminative abilities of others. Experimentally, we show that SMPE$^2$ outperforms a plethora of state-of-the-art MARL algorithms in complex fully cooperative tasks from the MPE, LBF, and RWARE benchmarks.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：在分布式部分可观测（Dec-POMDP）、无通信能力的合作多智能体环境中，每个智能体只能获取局部观测，难以推断全局状态，从而导致非平稳性、协作困难和探索低效。
- **动机**：现有 Agent Modeling（AM）方法存在若干不足：① 学习信念表示时未针对策略优化进行目标设计；② 未过滤冗余/非信息性的联合状态特征；③ 未利用推断出的表示来改善初始探索策略，尤其在稀疏奖励任务中表现不佳。
- **目标**：研究两个核心问题——Q1：智能体能否从自身观测中推断出对策略有用的状态信念表示；Q2：能否利用这些表示实现高效探索，发现更好的合作策略。

## 2. 方法论
- **核心思想**：提出**状态建模（State Modelling, SM）**框架，让智能体在部分可观测条件下，以优化自身策略为目标，从局部观测中推断出有意义的信念表示 \( z_i \)，并过滤联合状态中的冗余信息。在此基础上提出**SMPE²**算法，包含显式和隐式两种增强方式：
  - **显式**：将信念 \( z_i \) 直接输入策略网络，增强状态辨别能力。
  - **隐式**：通过对抗式内在探索奖励，鼓励智能体发现新颖、高价值的状态，同时提升其他智能体的推断能力。
- **关键技术细节**：
  - **自监督状态建模**：使用变分编码器-解码器（ED），以自监督方式学习从 \( o_i \) 到 \( z_i \) 的映射，重建其他智能体的观测 \( o_{-i} \)。引入**AM过滤器** \( w_{ij} \)（通过MLP和sigmoid输出0-1权重）逐元素加权重建目标，过滤非信息性特征，仅保留可推断、对策略有用的部分。
  - **损失函数**：总编码损失包含重建损失（\( L_{rec} \)）、KL散度正则化（\( L_{KL} \)）、过滤器范数正则化（\( L_{norm} \)），以及一个额外的critic损失（\( L_{w\_critic} \)）来促使过滤器与策略优化关联。
  - **对抗计数探索**：在信念空间 \( Z_i \) 上使用 SimHash 计数，为每个智能体计算内在奖励 \( \hat{r}_i = 1/\sqrt{n(s)} \)，鼓励发现新观测（进而新信念），同时隐含地增加其他智能体重建模型的难度，促进集体探索。
  - **算法架构**：基于 MAA2C（CTDE）搭建，每个智能体使用带 \( z_i \) 的独立Actor，两个Critic（一个标准值函数，一个基于过滤状态 \( \hat{s} \) 的值函数）。
- **公式/算法流程**（文字说明）：参见论文 Algorithm 1（附录F），核心循环包括：收集轨迹、计算内在奖励、更新Actor、更新两个Critic、定期更新ED参数和过滤器目标参数。

## 3. 实验设计
- **数据集/场景**：
  - **MPE**：Spread（3/4/5/8个agent）、Double Speaker-Listener。
  - **LBF**：6种任务，如2s-9x9-3p-2f、4s-11x11-3p-2f等，含稀疏奖励。
  - **RWARE**：tiny-2ag-hard、tiny-4ag-hard、small-4ag-hard。
- **Benchmark**：广泛使用的合作MARL基准，常被用于评估探索与协作能力。
- **对比方法**：
  - 基础RL：MAA2C、COMA、MAPPO、ATM（Transformer）。
  - 探索方法：EOI、EMC、MASER。
  - 建模方法：SIDE、MLIAM（多智能体扩展的LIAM）。
- **实验设置**：6个随机种子，报告25%-75%置信区间；MPE/LBF每实验10M步，RWARE 40M步。

## 4. 资源与算力
- 论文未明确说明所有实验的GPU型号、数量及总训练时长。
- 仅在附录E.4.12中给出单次运行时间对比（使用GPU RTX 3080ti、CPU i9-11900、64GB RAM），示例任务为LBF 2s-12x12-2p-2f：SMPE²运行1h13min，而EMC需1天5h，MASER需1天1h。
- 因此，整体算力消耗未系统披露。

## 5. 实验数量与充分性
- **实验数量**：在三大基准上共约20+个任务场景（MPE 5种、LBF 6种、RWARE 3种，加上消融变体）。消融研究涵盖：组件选择（无内在奖励、无过滤器、无KL、无L2范数、替换探索方案）、策略优化关联性、过滤器重要性、不同超参数（\( \lambda_{rec}, \lambda_{norm} \)）、t-SNE可视化、与SIDE/MLIAM对比、不同Backbone灵活性测试。
- **充分性与公平性**：
  - 对比方法均为SOTA，代码来自原论文或公开库。
  - 报告了置信区间，多次随机种子。
  - 消融实验较全面，验证了各模块贡献。
  - 但未包含超大规模场景（如100+agent），也未与基于通信的方法比较（因设定无通信）。

## 6. 主要结论与发现
- SMPE²在所有基准上均优于对比方法，尤其在LBF和RWARE的困难稀疏奖励任务中，显著超越其他方法，部分任务（如2s-9x9-3p-2f、4s-11x11-3p-2f）几乎被完全解决。
- 状态建模和AM过滤器能有效提取对策略有用的信念表示，过滤冗余信息；对抗式内在探索进一步提升了联合探索效率。
- t-SNE可视化表明，加入KL正则化可使不同智能体的信念空间更连贯、易协作；否则信念离散，协作变差。
- 消融证实：过滤器、第二critic、内在奖励、KL项均对性能有重要贡献。

## 7. 优点
1. **方法新颖**：将状态表示学习与策略优化直接耦合（不同于以往的辅助任务），并引入自适应过滤器处理冗余信息。
2. **探索机制创新**：利用信念空间进行对抗式内在奖励，既鼓励个体探索又促进同伴建模。
3. **灵活性**：可不同MARL Backbone（如MAA2C、MAPPO）结合，且无需额外通信或对观测特征的先验知识。
4. **实验全面**：在多个基准、多种难度任务上验证，消融细致，可视化有说服力。
5. **效率**：运行时间远低于EMC、MASER等复杂探索方法（参见附录运行时间表）。

## 8. 不足与局限
1. **性能验证范围**：未在超大规模（如数百agent）或更复杂的随机环境中测试；未与基于通信的方法对比（设定为无通信）。
2. **计算开销**：引入额外ED、过滤器、第二critic，参数量和训练步骤增加；未给出完整训练的总GPU小时数。
3. **超参数敏感性**：\( \lambda_{rec}, \lambda_{norm}, \lambda_{KL}, \beta \) 等需调参；消融显示某些值偏离会影响性能。
4. **理论保证**：虽证明状态建模目标与原始Dec-POMDP等价，但实际优化仍依赖近似；滤波器收敛性未严格分析。
5. **应用限制**：假设部分可观测但可共享所有agent观测进行训练（CTDE），在严格隐私或带宽受限场景可能不适用；未来需考虑随机观测噪声或复杂动力学的适应性。

（完）
