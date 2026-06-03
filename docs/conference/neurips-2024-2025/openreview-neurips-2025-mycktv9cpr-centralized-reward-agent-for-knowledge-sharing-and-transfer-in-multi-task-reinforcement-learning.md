---
title: Centralized Reward Agent for Knowledge Sharing and Transfer in Multi-Task Reinforcement Learning
title_zh: 多任务强化学习中用于知识共享与迁移的中央奖励代理
authors: "Haozhe Ma, Zhengding Luo, Thanh Vinh Vo, Kuankuan Sima, Tze-Yun Leong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MyCKtV9CpR"
tags: ["query:graph-part"]
score: 6.0
evidence: 多任务强化学习中采用中央奖励代理和分布式策略代理进行知识共享
tldr: 在稀疏奖励的多任务强化学习中，本文提出中央奖励代理（CRA）框架，将CRA作为知识池，从各任务蒸馏知识并以奖励形式分发给分布式策略智能体，从而提升学习效率和任务迁移能力。实验表明该方法在多个连续控制任务中显著加速学习并适应新任务。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1456, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1358, \"height\": 1480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1356, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mycktv9cpr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1391, \"height\": 845, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mycktv9cpr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mycktv9cpr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mycktv9cpr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 1047, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mycktv9cpr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mycktv9cpr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1249, \"height\": 1027, \"label\": \"Table\"}]"
motivation: 稀疏奖励问题需要有效的知识共享机制来提高多任务学习效率。
method: 设计中央奖励代理从各任务提取知识并生成辅助奖励，分发给分布式策略智能体。
result: 在多任务环境中加速学习，并成功迁移至新任务。
conclusion: 基于奖励的知识共享能有效提升多任务强化学习的性能。
---

## Abstract
Reward shaping is effective in addressing the sparse-reward challenge in reinforcement learning (RL) by providing immediate feedback through auxiliary, informative rewards. Based on the reward shaping strategy, we propose a novel multi-task reinforcement learning framework that integrates a centralized reward agent (CRA) and multiple distributed policy agents. The CRA functions as a knowledge pool, aimed at distilling knowledge from various tasks and distributing it to individual policy agents to improve learning efficiency. Specifically, the shaped rewards serve as a straightforward metric for encoding knowledge. This framework not only enhances knowledge sharing across established tasks but also adapts to new tasks by transferring meaningful reward signals. We validate the proposed method on both discrete and continuous domains, including the representative Meta-World benchmark, demonstrating its robustness in multi-task sparse-reward settings and its effective transferability to unseen tasks.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在强化学习中，稀疏奖励环境导致智能体缺乏即时反馈，探索效率低下；多任务强化学习（MTRL）中，现有知识迁移方法（如策略蒸馏、表示共享、参数共享）存在适应慢、利用不充分等问题。
- **整体含义**：论文提出将奖励塑造（Reward Shaping）与多任务学习相结合，利用辅助密集奖励作为知识载体，实现任务间知识的有效共享与迁移，同时缓解稀疏奖励挑战。该方法在多个连续/离散控制任务上验证了其提升学习效率和可迁移性的能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计一个**中央奖励代理（Centralized Reward Agent, CRA）**作为知识池，从多个分布式策略智能体中收集经验，提取通用任务知识，并以**知识奖励（knowledge reward）**的形式分发给各策略智能体，增强其原始环境奖励。
- **关键技术细节**：
  - **CRA建模**：CRA是一个自包含的RL智能体，其策略`π_rwd`将状态-动作对`(s, a)`映射到连续奖励值`r_knw`，奖励范围`[R_min, R_max]`。采用离策略actor-critic算法优化。
  - **知识奖励集成**：每个策略智能体`A_pol_i`的增强奖励为`r_pol_i = r_env_i + λ * r_knw`，其中`λ`为缩放因子。
  - **信息同步机制**：为平衡多任务学习，引入**相似性权重**和**性能权重**，控制CRA从各任务回放缓冲区采样的比例。
    - 相似性权重`w_sim`：基于各任务策略网络隐藏层的特征（经ReLU激活），计算与聚类质心的注意力分数。
    - 性能权重`w_per`：基于最近`K`步环境奖励的平均值。
    - 最终采样权重`w = α * w_sim + (1 - α) * w_per`。
  - **算法流程**：每个迭代中，各策略智能体与环境交互收集转移，CRA生成知识奖励并存储；策略智能体使用增强奖励更新；计算采样权重后，CRA从联合回放缓冲区采样子集进行更新。CRA与策略智能体异步更新。

## 3. 实验设计：数据集/场景、基准、对比方法

- **实验场景**：
  - **Meta-World**：`ML10-sparse`（10个训练任务+5个测试任务）和`ML50-sparse`（45个训练任务+5个测试任务）。
  - **2DMaze**：4个训练任务+1个测试任务。
  - **3DPickup**：4个训练任务+1个测试任务。
  - **MujocoCar**：4个训练任务+1个测试任务。
  - 所有任务均提供稀疏环境奖励（成功得1，否则0）。
- **基准（baselines）**：
  - 基础RL算法：DQN（离散）、SAC（连续）。
  - ReLara（每个策略配独立奖励代理，无跨任务共享）。
  - TD-MPC2、CMTA、PiCor、MCAL、PaCo、SC、SoftModule。
- **评估指标**：最终平均回报（100个episode，10个随机种子），并报告标准误差。

## 4. 资源与算力

- **文中明确说明**：实验在计算集群上进行，硬件配置为：Ubuntu 20.04 OS，2×Intel Xeon Gold 6326 CPU，256GB RAM，1×NVIDIA A100 20GB GPU，Super Micro 2022服务器。
- **未提及**：具体训练时长或总计算量，仅给出单次运行的“burn-in steps”等超参数。

## 5. 实验数量与充分性

- **实验组数**：
  - 多任务学习对比实验：在4个领域（ML10、ML50、2DMaze、3DPickup、MujocoCar）上，每个方法运行10个随机种子，报告平均回报和标准误差。
  - 新任务迁移实验：使用已训练的CRA，对比“CRA w/学习”、“CRA w/o学习”、ReLara、基础算法。
  - 消融实验：研究采样权重的影响，对比不同α值（0.25, 0.5, 0.75）以及去除单一权重或全部权重的变体，在2DMaze、3DPickup、MujocoCar上报告每个子任务的回报和方差。
  - 可视化分析：展示2DMaze中最大知识奖励对应的动作方向。
- **充分性与客观性**：
  - 覆盖离散和连续控制、多任务数目差异（10/50/4），验证鲁棒性。
  - 使用10个种子降低随机性影响；报告标准误差；在多任务场景下比较了多种SOTA方法。
  - 消融实验验证了信息同步机制的有效性，并展示了各任务的个体表现和平衡性。
  - 实验设计较为全面，但缺乏与更多最新方法的对比（如基于transformer的MTRL方法），也未记录运行时间等效率指标。

## 6. 论文的主要结论与发现

- **主要结论**：CenRA框架在多任务稀疏奖励环境下显著优于所有基线方法，获得最高平均回报且收敛更快、波动更小。
- **知识迁移能力**：将训练好的CRA应用于新任务时，即使不继续学习（CRA w/o learning）也优于重新训练奖励代理的ReLara和基础算法；若CRA继续学习，则性能最高。
- **信息同步机制的重要性**：去除采样权重会导致各任务回报方差增大、整体性能下降；同时使用相似性和性能权重能维持系统平衡，其中性能权重影响更大。
- **奖励可视化**：CRA能够学习到与任务目标一致的语义奖励（如走向钥匙、走向门），有效指导探索。

## 7. 优点

- **创新性**：将奖励塑造融入多任务学习，以密集奖励作为知识传递媒介，直接缓解稀疏奖励问题。
- **灵活性**：策略智能体可使用任意合适的RL算法（on/off-policy），CRA独立训练，易于集成。
- **知识共享机制**：通过中央奖励池和采样权重，实现任务间知识的高效蒸馏与平衡分配。
- **迁移能力**：CRA可被直接复用于新任务，无需重新训练，且可通过持续学习进一步提升。
- **实验详实**：涵盖多种任务规模、离散/连续控制、丰富的基线对比和消融分析。

## 8. 不足与局限

- **维度一致性要求**：CRA要求所有任务的状态和动作维度相同，限制了在异构任务空间的直接应用（论文提出将来可引入预处理技术）。
- **权重平衡局限**：固定超参数α可能不是最优，未能实现自适应调节；性能权重可能压制高绩效任务的潜力。
- **计算开销**：未对比训练时间或计算效率，CRA和多个策略智能体的交替更新可能增加开销。
- **实验覆盖**：缺少与更多最新MTRL方法（如基于元学习、零样本迁移）的对比；未在真实机器人或更高维复杂任务上验证。
- **理论保证**：未提供收敛性或最优性理论分析，主要依赖实验评估。

（完）
