---
title: Offline Goal-conditioned Reinforcement Learning with Quasimetric Representations
title_zh: 基于拟度量表示的离线目标条件强化学习
authors: "Vivek Myers, Bill Zheng, Benjamin Eysenbach, Sergey Levine"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=P23UMiw7iJ"
tags: ["query:graph-part"]
score: 9.0
evidence: 离线目标条件强化学习拟度量表示方法
tldr: 该文针对离线目标条件强化学习中的表示学习问题，提出了融合对比表示和时间距离两种框架的统一方法。通过拟度量空间的三角不等式约束学习后继表示，使得算法能够更有效地从离线数据中提取目标到达策略。实验表明该方法在多个离线目标达成任务中取得了最优性能。该工作为强化学习中的表示学习提供了新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-p23umiw7ij/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p23umiw7ij/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p23umiw7ij/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 730, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p23umiw7ij/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p23umiw7ij/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 886, \"height\": 752, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 671, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1197, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1120, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 711, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 759, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p23umiw7ij/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 477, \"height\": 227, \"label\": \"Table\"}]"
motivation: 现有目标条件强化学习表示方法未能充分利用两种主流框架的优势。
method: 利用拟度量空间的三角不等式约束，统一对比表示和时间距离框架来学习后继表示。
result: 在离线目标条件任务上实现更优的目标达成策略。
conclusion: 提出的统一表示方法有效提升了离线强化学习的目标达成能力。
---

## Abstract
Approaches for goal-conditioned reinforcement learning (GCRL) often use
learned state representations to extract goal-reaching policies. Two
frameworks for representation structure have yielded particularly
effective GCRL algorithms: (1) *contrastive representations*, in which
methods learn "successor features" with a contrastive objective that
performs inference over future outcomes, and (2) *temporal distances*,
which link the (quasimetric) distance in representation space to the
transit time from states to goals. We propose an approach that unifies
these two frameworks, using the structure of a quasimetric
representation space (triangle inequality) with the right additional
constraints to learn successor representations that enable optimal
goal-reaching. Unlike past work, our approach is able to exploit a
**quasimetric** distance parameterization to learn **optimal**
goal-reaching distances, even with **suboptimal** data and in
**stochastic** environments. This gives us the best of both worlds: we
retain the stability and long-horizon capabilities of Monte Carlo
contrastive RL methods, while getting the free stitching capabilities of
quasimetric network parameterizations. On existing offline GCRL
benchmarks, our representation learning objective improves performance
on stitching tasks where methods based on contrastive learning struggle,
and on noisy, high-dimensional environments where methods based on
quasimetric networks struggle.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Offline Goal-conditioned Reinforcement Learning with Quasimetric Representations》的详细中文总结。

### 1. 论文的核心问题与整体含义
- **研究动机**：离线目标条件强化学习（GCRL）通常依赖学习到的状态表示来提取目标到达策略。当前有两类主流框架各有优劣：
    - （1）**对比表示**（如 Contrastive RL, CRL）通过蒙特卡洛方式学习后继特征，在长程任务中稳定，但难以利用次优数据拼接出更短路径（stitching）。
    - （2）**时间距离**（如 Quasimetric RL, QRL）通过拟度量网络的三角不等式结构天然支持路径拼接，但在随机环境或次优数据下无法学到最优距离。
- **整体意义**：论文旨在统一上述两种框架，同时获得对比表示的稳定性和长程能力，以及拟度量网络“免费”的拼接能力，从而在随机环境、次优数据下也能学到最优目标到达距离。

### 2. 论文提出的方法论
- **核心思想**：Temporal Metric Distillation (TMD) 通过强制距离函数满足三个不变性来恢复最优后继距离 \(d_{SD}^*\)：
    1. **三角不等式**（P-不变性）：通过拟度量网络架构（如 MRNe）自动满足。
    2. **动作不变性**（I-不变性）：\(d(s, (s,a)) = 0\)，即状态与自身状态-动作对之间的距离为零，通过损失 \(L_I\) 强制。
    3. **时间不变性**（T-不变性）：\(e^{-d(\phi(s,a), \psi(g))} = \mathbb{E}_{s' \sim P(\cdot|s,a)} [\gamma e^{-d(\psi(s'), \psi(g))}]\)，通过 Bregman 散度损失 \(L_T\) 强制。
- **关键技术细节**：
    - 先用**对比学习**（backward NCE loss \(L_{NCE}\)）初始化距离 \(d_\theta = d_{SD}^{\pi_\beta}\)（行为策略的后继距离）。
    - 然后通过联合优化 \(L_{TMD} = L_{NCE} + \zeta (L_I + L_T)\) 逐步收紧距离，从而收敛到最优距离 \(d_{SD}^*\)（理论证明见 Theorem 3）。
    - 距离参数化采用 Metric Residual Network (MRN)，保证三角不等式。
    - 策略提取时结合行为克隆约束（类似于 TD3+BC 的做法），使用损失 \(L_\pi\)。
- **算法流程**（文字描述）：
    1. 从离线数据集采样批次 \(B = \{s_i, a_i, s'_i, g_i\}\)。
    2. 用目标网络 \(\bar{\psi}\) 停止梯度，计算 \(L_{NCE}, L_I, L_T\) 并更新状态编码器 \(\psi\) 和状态-动作编码器 \(\phi\)。
    3. 用当前距离 \(d_\theta\) 通过最小化 \(L_\pi\) 更新策略 \(\pi\)。

### 3. 实验设计
- **数据集与场景**：使用 OGBench 基准，包含多种连续控制和视觉任务，例如 humanoidmaze、antmaze、pointmaze 以及 visual_antmaze 等，涵盖导航、拼接、随机传送（teleport）等子任务。
- **对比方法**：
    - 行为克隆方法：GCBC (Goal-Conditioned Behavioral Cloning)
    - 离线 RL 方法：GCIQL, GCIVL
    - 对比方法：CRL (Contrastive RL)
    - 拟度量方法：QRL (Quasimetric RL)
    - 另一种度量蒸馏方法：CMD (Contrastive Metric Distillation，缺少 T/I 不变性)
- **评价指标**：成功率（Success Rate），每个环境报告 5 个目标任务的聚合结果，6 个随机种子，附带标准误差。

### 4. 资源与算力
- 文本中明确说明：使用 NVIDIA A6000 GPU（48GB 显存），每个实验配备 4 个 CPU 核心和 1 个 GPU。每个基于状态的实验约需 2 小时，每个像素级实验约需 4 小时。未说明并发实验的总 GPU 数量，但单实验资源已具体给出。

### 5. 实验数量与充分性
- **实验数量**：在表 1 中报告了 16 个环境/数据集组合上的结果，每个 6 个种子，共约 96 次独立运行。另外在消融研究（图 4、表 4）中测试了去除各损失分量的效果，以及不同 Bregman 散度的比较（表 5）。实验覆盖了不同难度、不同动力学特性的场景。
- **充分性与客观性**：实验设计较为全面，涵盖了论文声称的核心优势（拼接、随机性、长程）；使用统一基准 OGBench，基线结果直接引用官方参考实现，保证了公平性。消融实验验证了各个组件的重要性。存在一些主观的选择（如超参数 ζ 的设定），但论文对此进行了讨论并给出了经验指导。

### 6. 论文的主要结论与发现
- TMD 在拼接任务（如 antmaze_large_stitch）上显著优于 CRL 和 QRL，表明其能够利用拟度量架构拼接行为。
- 在随机环境（如 pointmaze_teleport_stitch）上，TMD 的表现远好于 QRL（先前方法在此类任务上失败），验证了 T 不变性在处理随机动力学时的有效性。
- 消融实验证实：失去对比损失、T 损失或 I 损失都会导致性能大幅下降，证明三者的协同作用不可或缺。
- 理论分析（定理 3）保证了 TMD 能收敛到最优后继距离，提供了深厚的基础。

### 7. 优点
- **理论严谨**：完整证明了 TMD 算子收敛到最优距离，并给出了不动点唯一性的证明。
- **设计巧妙**：通过识别和强制三个关键不变性，巧妙地将对比学习和拟度量学习统一起来，同时克服了各自的弱点。
- **实证强大**：在多个基准上取得领先结果，尤其擅长拼接与随机环境，且超参数相对稳定。
- **可复现性**：公开了代码，提供了详细的超参数和网络配置。

### 8. 不足与局限
- **超参数敏感性**：权重 ζ 需要根据环境手动调整（中等运动环境 0.01，其他 0.1），缺乏自适应调整方法。
- **策略提取分离**：距离学习与策略提取是分开优化的，论文指出将两者更直接整合可能会带来额外的收益。
- **架构限制**：使用的 MRN 架构可能不是最表达力的拟度量参数化，更先进的架构（如 IQE）可能进一步提升性能。
- **可解释性与风险**：虽然模型规模不大，但长程决策能力可能带来潜在的隐蔽风险（如不可预见的错误行为），且距离函数的可解释性有限。
- **实验覆盖**：主要测试了模拟环境中的机械臂和迷宫任务，未涉及真实机器人或更复杂的高维任务（如视频游戏），泛化性尚需验证。

（完）
