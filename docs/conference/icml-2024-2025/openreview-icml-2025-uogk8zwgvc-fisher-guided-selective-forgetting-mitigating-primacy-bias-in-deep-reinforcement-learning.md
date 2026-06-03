---
title: "Fisher-Guided Selective Forgetting: Mitigating Primacy Bias in Deep Reinforcement Learning"
title_zh: Fisher引导的选择性遗忘：缓解深度强化学习中的首因偏差
authors: "Massimiliano Falzari, Matthia Sabatelli"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=uOGK8zwgvc"
tags: ["query:graph-part"]
score: 9.0
evidence: 深度强化学习方法缓解首因偏差
tldr: 深度强化学习常因过度依赖早期经验而产生首因偏差，损害学习效率。本文通过Fisher信息矩阵刻画偏差模式，提出选择性遗忘方法FGSF，在复杂环境中显著提升了DRL的最终性能和学习速度，揭示了参数空间几何结构对偏差的影响。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 812, \"height\": 1171, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 910, \"height\": 1173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 809, \"height\": 1174, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 1172, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 810, \"height\": 1186, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1046, \"height\": 1502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1037, \"height\": 1505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1031, \"height\": 1513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1047, \"height\": 1510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1047, \"height\": 1511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1047, \"height\": 1504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uogk8zwgvc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1017, \"height\": 1506, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-uogk8zwgvc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1175, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uogk8zwgvc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 941, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uogk8zwgvc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1175, \"height\": 531, \"label\": \"Table\"}]"
motivation: 深度强化学习中的首因偏差导致过拟合早期经验。
method: 基于Fisher信息矩阵的几何结构，选择性调整网络权重，遗忘早期经验。
result: 在复杂环境中有效缓解首因偏差，提升性能。
conclusion: FGSF为理解与缓解DRL中的偏差提供了新工具。
---

## Abstract
Deep Reinforcement Learning (DRL) systems often tend to overfit to early experiences, a phenomenon known as the primacy bias (PB). This bias can severely hinder learning efficiency and final performance, particularly in complex environments.
This paper presents a comprehensive investigation of PB through the lens of the Fisher Information Matrix (FIM). We develop a framework characterizing PB through distinct patterns in the FIM trace, identifying critical memorization and reorganization phases during learning. Building on this understanding, we propose Fisher-Guided Selective Forgetting (FGSF), a novel method that leverages the geometric structure of the parameter space to selectively modify network weights, preventing early experiences from dominating the learning process. 
Empirical results across DeepMind Control Suite (DMC) environments show that FGSF consistently outperforms baselines, particularly in complex tasks. We analyze the different impacts of PB on actor and critic networks, the role of replay ratios in exacerbating the effect, and the effectiveness of even simple noise injection methods. 
Our findings provide a deeper understanding of PB and practical mitigation strategies, offering a FIM-based geometric perspective for advancing DRL.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：深度强化学习（DRL）系统存在 **首因偏差（Primacy Bias, PB）**，即过度依赖早期经验，导致后期难以适应新信息，损害学习效率和最终性能，尤其在复杂环境中更为严重。
- **研究动机**：现有缓解方法（如网络周期性重置、噪声注入）缺乏对PB内在机制的理解，且通常需要在稳定性和性能之间权衡。论文希望通过信息几何视角（Fisher信息矩阵）深入刻画PB的动态特征，并设计有理论依据的缓解策略。
- **整体含义**：为DRL中的偏差问题提供了一种新的几何理解与实用工具，推动了更鲁棒、高效的学习算法的开发。

#### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：利用 **Fisher信息矩阵（FIM）** 量化参数空间的局部几何结构，识别PB的两个典型学习阶段（记忆阶段→重组阶段），并借鉴机器遗忘中的 **选择性遗忘（Selective Forgetting）** 框架，通过FIM引导的权重擦除（weight scrubbing）来削弱早期经验的过度影响。
- **关键技术细节**：
  - **PB的两阶段特征**：
    - **记忆阶段**：FIM迹快速指数上升，表示参数对早期信息的高敏感吸收。
    - **重组阶段**：FIM迹持续下降，尽管性能提升，但参数对后续新信息敏感性降低，表明早期经验固化。
  - **选择性遗忘公式**：基于Golatkar等人的遗忘拉格朗日框架，采用 **FIM近似** 的权重更新：
    \[
    S(w) = w + (\lambda\sigma^2)^{1/4} F^{-1/4} \epsilon
    \]
    其中 \(F\) 为当前批次的经验FIM（使用EKFAC高效近似），\(\epsilon\) 为标准高斯噪声，\(\lambda\) 为遗忘系数（控制遗忘强度）。原公式中的梯度项被省略，因为标准梯度下降已承担类似更新，且周期性擦除不适用于一次性全梯度。
  - **算法流程**（Algorithm 1）：
    1. 从回放缓冲区采样批次，使用DRL算法（如SAC）更新网络参数。
    2. 每固定步数 \(F\)（论文中设为10）执行一次擦除：计算当前批次的FIM，添加结构化的噪声扰动。
    3. 可分别应用于actor和critic网络；实验发现critic-only scrubbing效果更优。
- **核心创新**：将信息几何与机器遗忘结合，提出针对性、可调参数（\(\lambda\)、频率 \(F\)）的PB缓解方法。

#### 3. 实验设计：数据集/场景、基准、对比方法
- **数据集/场景**：**DeepMind Control Suite (DMC)** 中的10个连续控制任务，分为三类：
  - 基本控制：Pendulum, Acrobot
  - 运动任务：Humanoid, Quadruped, Walker, Cheetah, Hopper, Swimmer
  - 操作任务：Reacher, Finger
- **基准算法**：**Soft Actor-Critic (SAC)**（默认超参数）。
- **对比方法**：
  - **标准SAC**（基线）
  - **周期性网络重置方法**（Nikishin et al., 2022）：每2×10⁵步重置网络参数。
  - **自我消融**：
    - Critic-only scrubbing vs. Full scrubbing
    - FGSF vs. 简单高斯噪声注入（均值为0，标准差为参数均值乘以0.001）
- **评估指标**：最终100幕平均回报（5个随机种子）、学习曲线、FIM迹演化、参数更新量（KL散度）、休眠神经元比例等。

#### 4. 资源与算力
- **未明确说明**：论文没有提及使用的GPU型号、数量、训练时长等具体资源信息。仅在附录E中提及 **FGSF相比基础SAC增加了15-20%的训练时间**（由于FIM计算开销），但未给出绝对时间值（如小时数）。因此无法量化算力投入。

#### 5. 实验数量与充分性
- **实验数量**：覆盖面较广，主要包括：
  - 10个DMC环境的性能对比（每个5个种子）。
  - 超参数 \(\lambda\) 敏感性分析（三个值：5×10⁻⁶, 5×10⁻⁷, 5×10⁻⁸）。
  - 重放比例鲁棒性测试（2和4）。
  - Critic-only vs. Full scrubbing 消融实验。
  - FGSF vs. 高斯噪声对比实验。
  - 附加分析：FIM迹、KL散度、休眠神经元、计算开销（附录）。
- **充分性与客观性**：
  - **充分性良好**：覆盖了不同复杂度环境、关键超参数、网络组件、不同噪声类型，并提供了统计方差（用5个种子）。
  - **客观性存在轻微不足**：所有实验仅基于SAC算法，未验证在TD3、PPO等其他DRL方法上的泛化性；未报告在大型或真实世界环境中的结果。此外，Acrobot环境中所有方法均失败（得分极低），可能暗示超参数适配问题，作者未深入解释。
  - **公平性**：对比方法的重置频率（每2×10⁵步）和FGSF的擦除频率（每10步）不一致，但作者在讨论中承认这种差异是设计选择，并分析了其影响。

#### 6. 论文的主要结论与发现
- **性能提升**：在复杂环境（Humanoid, Quadruped）中，FGSF相比基线SAC最高提升50%回报（Humanoid: 150 vs. 95），且优于重置方法。
- **Critic更易受PB影响**：Critic-only scrubbing即可达到甚至优于Full scrubbing的性能，表明Critic是PB的关键载体。
- **稳定性和样本效率**：FGSF学习曲线更平滑，无性能骤降（重置方法有），且早期样本效率更高（提前约2×10⁵步达到90%最佳性能）。
- **鲁棒性**：在高重放比例（2和4）下，FGSF保持稳健，而基线SAC性能急剧下降。
- **FIM迹证据**：FGSF成功抑制了早期FIM迹的峰值（Critic从2×10⁶降至5×10⁵），符合缓解PB的特征。
- **简单噪声亦有效**：高斯噪声注入也能提升基线性能，但FGSF更稳定，估值结构的FIM引导更优。

#### 7. 优点
- **理论创新**：首次用FIM的几何特征量化PB的两阶段动态，为理解偏差提供了新工具。
- **方法原理性**：结合信息几何与机器遗忘，推导出具有理论基础的权重擦除公式，而非启发式重置或随意噪声。
- **实验全面**：覆盖多维度分析（环境复杂度、超参数、网络组件、重放比、噪声类型、M领域指标），结论可信。
- **计算效率**：采用EKFAC近似FIM，将额外训练开销控制在15-20%，可接受范围。
- **实用指导**：给出\(\lambda\)推荐初值（5×10⁻⁷），并说明调整策略，便于复现和应用。

#### 8. 不足与局限
- **计算开销**：虽然受控，但15-20%额外时间在资源受限场景仍可能成为瓶颈（未提供GPU型号和绝对时长，难以评估实际成本）。
- **超参数敏感性**：\(\lambda\)的取值依赖环境和教师信号，论文仅测试三个值，未给出自动化调整机制。简单环境（Acrobot）中所有方法失败，提示FGSF不一定普适。
- **泛化性有限**：仅在SAC上验证，未在TD3、PPO等算法或更广泛的领域（如Atari、机器人现实任务）测试。
- **休眠神经元分析**：实验发现FGSF并未降低休眠神经元比例，反而持平或更高，挑战了该指标与PB的关联，作者虽提及但未深入解释。
- **资源报告缺失**：未提供GPU型号、训练时长等细节，影响结果的可复现性和能耗评估。
- **被拒稿背景**：根据原论文元数据标注为ICML-2025-Rejected-Public，需注意该工作可能尚未通过同行评审成熟度验证。

（完）
