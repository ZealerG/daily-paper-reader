---
title: "The Courage to Stop: Overcoming Sunk Cost Fallacy in Deep Reinforcement Learning"
title_zh: 停止的勇气：在深度强化学习中克服沉没成本谬误
authors: "Jiashun Liu, Johan Obando-Ceron, Pablo Samuel Castro, Aaron Courville, Ling Pan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=VzC3BAd9gf"
tags: ["query:graph-part"]
score: 9.0
evidence: 深度强化学习算法，解决沉没成本谬误
tldr: 针对离线深度强化学习中重放缓冲区被低效数据污染的问题，本文提出LEAST机制，通过让智能体学会提前终止无用片段来克服沉没成本谬误。实验表明该方法提升了样本效率和最终性能，为深度RL的优化提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 840, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 834, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 827, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 779, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1656, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 850, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 834, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 844, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 833, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 800, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 828, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 889, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1740, \"height\": 920, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1514, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vzc3bad9gf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1584, \"height\": 1151, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 1103, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 117, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 847, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 895, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 680, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 758, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vzc3bad9gf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1835, \"height\": 531, \"label\": \"Table\"}]"
motivation: 离线深度强化学习面临重放缓冲区被低效数据污染的问题，浪费环境交互。
method: 提出LEAST机制，让智能体学会在无信息片段中提前停止。
result: 在多个环境中验证了LEAST能提升样本效率和性能。
conclusion: 通过克服沉没成本谬误，深度RL训练更加高效。
---

## Abstract
Off-policy deep reinforcement learning (RL) agents typically leverage replay buffers for reusing past experiences during learning. This can help sample efficiency when the collected data is informative and aligned with the learning objectives; when that is not the case, it has the effect of ``polluting'' the replay buffer with data that can exacerbate optimization challenges in addition to wasting environment interactions due to redundant sampling. We argue that sampling these uninformative and wasteful transitions can be avoided by addressing the **sunk cost fallacy** which, in the context of deep RL, is the tendency towards continuing an episode until termination. To address this, we propose the *learn to stop* (**LEAST**) mechanism which uses statistics based on $Q$-values and gradient to guide early episode termination which helps agents recognize when to terminate unproductive episodes early. We demonstrate that our method improves learning efficiency on a variety of RL algorithms, evaluated on both the MuJoCo and DeepMind Control Suite benchmarks.

---

## 论文详细总结（自动生成）

# 论文总结：*The Courage to Stop: Overcoming Sunk Cost Fallacy in Deep Reinforcement Learning*

## 1. 核心问题与整体含义

- **研究动机**：在离线深度强化学习（Off-Policy Deep RL）中，智能体通常使用经验回放缓冲区（replay buffer）重复利用过去经验。然而，当收集到的数据信息量低或与学习目标不一致时，这些数据会“污染”缓冲区，导致样本效率下降，并浪费环境交互。论文指出，传统框架强制智能体完成整个情节（episode），即使已陷入次优轨迹仍需继续，这类似于认知科学中的“沉没成本谬误”（sunk cost fallacy）——因为已经投入了交互成本，就倾向于坚持到底，导致进一步浪费。
- **整体含义**：本文首次明确提出深度强化学习中存在沉没成本谬误，并提出一种轻量级机制 **LEAST**（Learn to Stop），赋予智能体提前终止无生产性情节的能力，从而提升学习效率和最终性能。这项工作开辟了一个新的优化方向：教会智能体何时“止损”。

## 2. 方法论

- **核心思想**：在环境交互过程中，动态评估当前轨迹的质量和学习潜力，当轨迹变得次优或已被充分学习时，智能体主动提前结束当前情节并重置环境，以节约交互预算并防止缓冲区被低效数据污染。
- **关键技术细节**：
  - **双准则自适应停止阈值**：
    - **质量准则（Q值）**：维护一个二维Q值缓冲区 \( B_Q \in \mathbb{R}^{K \times L} \)（K个最近情节，L为最大情节长度）。对于每个时间步 \( i \)，计算当前Q值 \( \hat{Q}_i \) 与历史中位数 \( \text{Median}(B_Q[:, i]) \) 的比较。
    - **学习潜力准则（梯度）**：同样维护梯度缓冲区 \( B_G \)，计算动态权重 \( \omega_i = \text{Median}(B_G[:, i]) / G_i \)（\( G_i \) 为当前梯度范数）。若当前梯度较大（表示新异状态），则 \( \omega_i < 1 \)，降低停止阈值，鼓励探索；反之则更严格。
    - **联合判定**：
      - 当 \( \epsilon_i \geq 0 \) 时，若 \( \hat{Q}_i < \omega_i \times \epsilon_i \)，则停止。
      - 当 \( \epsilon_i < 0 \) 时，使用 \( \omega_i^{-1} \) 修正，防止符号反转。
    - 使用中位数而非均值，对离群值更鲁棒。
  - **熵感知动态缓冲区大小**：每 \( c \) 步计算 \( B_Q \) 的熵 \( H(B_Q) \)，若当前熵 \( H_t > (1+\gamma) \times \bar{H} \)，则调整历史情节数量（增/减h个），以应对策略不稳定导致的数据分布剧烈变化。
  - **自适应探索噪声调节**：当早期停止频繁发生时（即策略可能陷入次优），根据近m个情节中在e步之前停止的频率，动态增加高斯探索噪声的标准差 \( \sigma \)，帮助智能体逃离当前行为模式（式4）。
- **算法流程**（以TD3为例，见Algorithm 1）：在固定长度情节的每一步，采样动作、存储经验、更新Q值和梯度缓冲区；当超过起始时间 \( t_{\text{start}} \) 后，每步计算阈值 \( \epsilon_i \) 和权重 \( \omega_i \)，若满足停止条件则提前终止并重置；同时更新演员-评论家网络。

## 3. 实验设计

- **基准环境**：
  - **MuJoCo**（OpenAI Gym）：四个经典连续控制任务（Ant, Walker2d, HalfCheetah, Humanoid等）。
  - **DeepMind Control Suite**：四个图像输入控制任务（Quadruped Run, Hopper Hop, Finger Turn Hard, Cartpole Swingup）。
  - **PointMaze**：一个具有长分支的迷宫任务，用于验证沉没成本谬误和样本效率。
- **对比方法**：
  - **主流算法**：TD3（确定性策略）、SAC（随机策略）、REDQ（集成评论家）、DroQ（带Dropout的SAC变体）。
  - **视觉RL基线**：DrQv2、CURL、A-LIX、TACO。
  - **消融实验**：对比仅用Q阈值、Q+梯度阈值、动态缓冲区、完整LEAST；对比中位数 vs 均值；对比不同超参数（\(\omega\)、\(\bar{\sigma}\)、e、\(\gamma\)、启动时间、初始集大小）。
- **评价指标**：归一化分数（max normalized score）、样本效率（达到基线最高分所需的训练步数）、最终性能分布（箱线图）。
- **公平性**：所有对比使用相同超参数、相同种子数（5个随机种子，部分10个），代码基于官方开源实现。

## 4. 资源与算力

- 论文在“Implementation Details”部分说明：所有实验使用 Python 3.8 和 PyTorch 1.12.1，运行在 **NVIDIA GeForce GTX 3090** GPU 上。
- 单次训练耗时：10小时到21小时不等（取决于算法和环境，如图像输入任务DrQv2比TD3更耗时）。
- 未明确给出总GPU数量或总计算小时数，但提到使用了多个GPU（未具体数字）。

## 5. 实验数量与充分性

- **实验组数**：
  - **主实验**：三大类算法（TD3、SAC、REDQ）在4个MuJoCo任务上（每个5种子） → 约4×3×5=60条学习曲线。
  - **视觉RL**：DrQv2在4个DMC任务上（每个5种子） → 约20条曲线。
  - **消融实验**：至少包括模块消融（4种变体）、阈值估计方法（均值vs中位数）、权重\(\omega\)敏感性（10个值）、噪声参数（\(\bar{\sigma}\)四种值、e四种值）、熵缩放系数\(\gamma\)（5种值）、启动时间（4种值）、初始集大小（4种值） → 每次5种子，总计数十组。
  - **额外实验**：长期学习任务（Humanoid Walk, 15M步）、更新比率（UTD）影响、FAU分析等。
- **充分性与公平性**：
  - 实验覆盖了主流算法类型（确定性、随机、集成）、经典连续控制和视觉任务，消融实验较为系统。
  - 所有对比均使用相同超参数、相同随机种子，并在“Experimental Setup”中明确列出参数来源。
  - 使用了5个随机种子（部分10个）并报告均值±标准差，统计可靠。
  - 论文承认超参数敏感性，并说明为避免计算开销而使用默认参数，但指出未来需更系统调参。
- **客观性评价**：实验设计相对充分，但视觉任务对比的基线（CURL、A-LIX、TACO）并非全部同架构，可能存在实现细节差异；未在更多环境（如Atari、机器人真实场景）验证，泛化性仍需考察。

## 6. 主要结论与发现

- **LEST显著提升样本效率和最终性能**：在MuJoCo上，TD3、SAC、REDQ结合LEAST后，学习曲线更快，最终得分更高（特别是Ant和Walker2d）；在DMC视觉任务中，DrQv2+LEAST比原始DrQv2快约30%收敛，性能接近TACO。
- **沉没成本谬误确实存在于深度RL中**：通过PointMaze实验，传统智能体被迫完成低效轨迹，而LEAST通过提前停止避免了无效交互，提高了缓冲区中信息性样本的比例。
- **双准则阈值（Q值+梯度）优于单准则**：消融实验表明，联合使用质量与学习潜力信号能使停止决策更合理。
- **中位数比均值更鲁棒**：在估计阈值时，中位数避免了异常Q值导致的频繁误停。
- **动态缓冲区大小和自适应噪声进一步改善稳定性**：熵感知的缓冲区调整和探索噪声调节使LEAST在多种任务上表现稳定。
- **LEAST有助于维持网络塑性**：长期训练任务（Humanoid）中，FAU指标下降更慢，表明连续学习能力得到保持。

## 7. 优点

- **概念创新**：首次将认知科学中的沉没成本谬误引入深度RL分析，并提出了一个简洁的解决方案。
- **方法轻量**：LEAST不增加额外网络模块，仅利用现成的Q值和梯度统计信息，计算开销小，易于集成到现有算法。
- **通用性强**：在三大类算法（TD3、SAC、REDQ）和视觉RL（DrQv2）上均取得一致提升，且超参数相对鲁棒。
- **实验系统**：包括主实验、消融、敏感性分析、长期训练、塑性分析，覆盖了多种维度，验证了方法的有效性。
- **可解释性**：通过可视化缓冲区数据分布（图3）和停止行为，直观展示了LEAST如何优化训练数据。

## 8. 不足与局限

- **稳定性风险**：论文指出LEAST可能增加得分方差（箱线图离群点更广），停止决策的突发性可能导致训练波动。
- **超参数敏感性**：虽然进行了敏感性分析，但部分参数（如\(\omega\)、启动时间、初始集大小）在不同任务上最优值不同，需要手工调整。论文承认“Too many sensitive parameters are also an issue to be optimized”。
- **实验覆盖不全**：仅在MuJoCo和DMC上验证，未包括Atari、机器人真实场景或高维离散控制任务，泛化性待进一步验证。
- **基线比较限制**：与CURL、A-LIX、TACO的比较中，这些方法使用了额外的网络模块（对比学习的特征编码器），而LEAST未附加网络，比较不够“公平”，但作者意图是表明LEAST作为轻量替代方案能达到相近性能。
- **计算资源未完全披露**：未给出总GPU数量或总训练小时数，不利于复现和能耗评估。
- **理论基础较浅**：停止准则的推导更多依赖经验观察，缺乏严格的数学证明（如最优停止时间是否存在唯一解）。作者也在未来工作中提到需要理论分析。
- **长期训练验证不足**：仅在Humanoid任务上测试了长期塑性（15M步），其他长期任务（如马拉松）未涉及。

（完）
