---
title: Reinforcement Learning with Segment Feedback
title_zh: 基于片段反馈的强化学习
authors: "Yihan Du, Anna Winnicki, Gal Dalal, Shie Mannor, R. Srikant"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=1XXqIIsgT3"
tags: ["query:graph-part"]
score: 6.0
evidence: 介于状态-动作和轨迹之间的新型强化学习反馈模型
tldr: 该论文提出一种介于单步奖励和轨迹奖励之间的反馈模型——片段反馈，将每幕划分为若干片段，仅在每个片段结束时给与奖励。理论分析表明该模型在长轨迹下比轨迹反馈更高效，并给出了学习算法和样本复杂度界限。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 525, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1496, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1225, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1356, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1196, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1xxqiisgt3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 867, \"height\": 571, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-1xxqiisgt3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 467, \"label\": \"Table\"}]"
motivation: 实用中为每个状态-动作收集奖励很困难，现存的轨迹反馈在长轨迹下效率低。
method: 提出片段反馈模型，仅在片段结束时给与奖励，并设计相应的学习算法。
result: 理论分析证明片段反馈在长轨迹下有更优的样本复杂度。
conclusion: 片段反馈平衡了反馈成本和学习效率，为实际RL应用提供新范式。
---

## Abstract
Standard reinforcement learning (RL) assumes that an agent can observe a reward for each state-action pair. However, in practical applications, it is often difficult and costly to collect a reward for each state-action pair. While there have been several works considering RL with trajectory feedback, it is unclear if trajectory feedback is inefficient for learning when trajectories are long. In this work, we consider a model named RL with segment feedback, which offers a general paradigm filling the gap between per-state-action feedback and trajectory feedback. In this model, we consider an episodic Markov decision process (MDP), where each episode is divided into $m$ segments, and the agent observes reward feedback only at the end of each segment. Under this model, we study two popular feedback settings: binary feedback and sum feedback, where the agent observes a binary outcome and a reward sum according to the underlying reward function, respectively. To investigate the impact of the number of segments $m$ on learning performance, we design efficient algorithms and establish regret upper and lower bounds for both feedback settings. Our theoretical and experimental results show that: under binary feedback, increasing the number of segments $m$ decreases the regret at an exponential rate; in contrast, surprisingly, under sum feedback, increasing $m$ does not reduce the regret significantly.

---

## 论文详细总结（自动生成）

# 基于片段反馈的强化学习（RL with Segment Feedback）论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：标准强化学习要求智能体在每一步（状态-动作对）后立即获得奖励，但在实际应用中（如机器人炒蛋、自动驾驶）为每个动作标注奖励极为困难且昂贵。现有工作提出仅在整条轨迹结束时给予一次反馈（轨迹反馈），但长轨迹下这种反馈信息过于稀疏，学习效率低下。
- **核心问题**：在“每步奖励”和“整条轨迹奖励”之间，是否存在一种中间粒度的反馈（例如将轨迹划分为若干片段，每段结束时给出一次反馈）？增加反馈的段数（即增加反馈频率）是否总能显著提升学习性能？不同反馈类型（二进制 vs. 求和）下的影响是否相同？
- **整体含义**：本文提出一个通用的“片段反馈”模型，从理论上严格证明了：在二进制反馈（如赞/踩）下，增加段数 $m$ 可使遗憾（regret）以指数速率下降；而在求和反馈下，增加 $m$ 对遗憾几乎没有影响。这一发现为实际应用中如何平衡反馈成本与学习效率提供了理论指导。

## 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：将每幕（episode）等分为 $m$ 个长度均为 $H/m$ 的片段，仅在每个片段结束时提供一次反馈。反馈分为两种：
    - **二进制片段反馈**：观测到一个二元结果 $y_{k,i} \sim \operatorname{Bernoulli}(\mu(\phi_{\tau_{k,i}}^\top \theta^*))$，其中 $\mu(x)=1/(1+e^{-x})$ 为 sigmoid 函数，$\phi_{\tau_{k,i}}$ 是该片段的状态-动作访问计数向量，$\theta^*$ 为未知奖励参数。
    - **求和片段反馈**：观测到该片段内随机奖励之和 $R_{k,i} = \phi_{\tau_{k,i}}^\top \theta^* + \text{噪声}$。
- **关键技术细节**：
    1. **二进制反馈**：设计 Thompson 采样风格的算法 **SegBiTS**（已知转移）和 **SegBiTS-Tran**（未知转移）。算法使用最大似然估计 (MLE) 估计奖励参数 $\hat\theta$，构造协方差矩阵 $\Sigma$，并添加高斯噪声 $\xi$ 产生后验参数 $\tilde\theta$，然后计算使 $\tilde\theta$ 下期望回报最大的策略。推导出遗憾上界含有 $\exp(H r_{\max} / (2m))$ 因子，且证明该指数依赖不可避免（下界）。
    2. **求和反馈**：设计基于线性上置信界 (LinUCB) 的算法 **E-LinUCB**（已知转移）和 **LinUCB-Tran**（未知转移）。算法使用最小二乘估计 $\hat\theta$，并借助 E-最优实验设计进行初始探索，使协方差矩阵的最小特征值最大，从而压缩置信椭圆半径。分析表明遗憾界中 $m$ 仅出现在对数项中，几乎不影响主阶。
- **公式与算法流程**（文字说明）：
    - **SegBiTS**：
        1. 收集历史片段数据，MLE 求解 $\hat\theta_{k-1}$。
        2. 计算协方差矩阵 $\Sigma_{k-1}$。
        3. 采样高斯噪声 $\xi_k \sim \mathcal{N}(0, \alpha \nu^2 \Sigma_{k-1}^{-1})$。
        4. 设定后验参数 $\tilde\theta_k = \hat\theta_{k-1} + \xi_k$。
        5. 通过任意 MDP 规划（如值迭代）求解 $\pi_k = \arg\max_\pi (\phi^\pi)^\top \tilde\theta_k$。
        6. 执行 $\pi_k$ 收集新数据。
    - **E-LinUCB**：
        1. 通过 E-最优设计计算策略分布 $w^*$，确定初始探索轮数 $K_0$。
        2. 执行 $K_0$ 轮初始探索，使 $\Sigma_{K_0}$ 可逆且最小特征值足够大。
        3. 对 $k>K_0$，用最小二乘求 $\hat\theta_{k-1}$，计算 UCB 值：$\hat\theta_{k-1}^\top \phi^\pi + \beta \|\phi^\pi\|_{\Sigma_{k-1}^{-1}}$，选取最大者对应的策略 $\pi_k$。
- **理论贡献**：给出了两套反馈下的遗憾上界和下界，揭示了 $m$ 的指数效应（二进制）和无关性（求和）。

## 3. 实验设计
- **数据集 / 场景**：论文未使用任何标准基准（如 Atari、DMControl 等），而是自己构造了小型表格型 MDP 实例，以便验证理论结果中的指数和对数趋势。
    - **二进制反馈实验**：9 个状态、5 个动作，含 good states 和 bad states，每幕长度 $H=100$，$r_{\max}=0.5$。
    - **求和反馈实验**：3 个状态、5 个动作，同样 $H=100$，$r_{\max}=0.5$，但因算法计算复杂度高（需枚举所有策略进行 E-最优设计），故意缩小状态数。
- **Benchmark**：无公开基准。作者仅对比自己提出的算法在不同 $m$ 下的表现，未与任何先前方法（如 Efroni et al. 2021、Chatterji et al. 2021）直接比较（因为那些工作仅针对轨迹反馈，且定义不同）。
- **对比方法**：算法自身在不同 $m$ 下的表现，并在二元反馈中对比已知转移（SegBiTS）和未知转移（SegBiTS-Tran）的差异；在求和反馈中对比 E-LinUCB 和 LinUCB-Tran。

## 4. 资源与算力
- 论文**未说明**使用的 GPU 型号、数量、训练时长等硬件资源。实验全部在 CPU 上即可完成（MDP 规模极小）。代码未公开。

## 5. 实验数量与充分性
- **实验数量**：每组实验进行了 20 次独立运行，绘制平均累计遗憾曲线（带 95% 置信区间）。二进制反馈中 $m$ 取 9 个值（1,2,4,5,10,20,25,50,100）；求和反馈中 $m$ 取相同值。
- **充分性评估**：实验规模较小，仅验证了理论中 $m$ 对遗憾的定性影响趋势（指数下降 vs. 几乎不变）。缺乏与基线方法的公平对比，未在复杂场景中测试，也未展示算法在更大 $|S|,|A|$ 时的可扩展性。因此**实验覆盖有限**，客观性尚可但不够充分。

## 6. 主要结论与发现
1. **二进制反馈**：增加片段数 $m$ 可使遗憾以 $\exp(H r_{\max} / (2m))$ 的指数速率下降；理论与下界匹配，说明这一指数依赖本质上是不可避免的。
2. **求和反馈**：增加 $m$ 几乎不影响遗憾主阶（仅通过 $\log(H/m)$ 少量影响），最优点在于 $m$ 保持为常量时即可达到最优遗憾 $O(\sqrt{|S||A| H K})$。
3. **未知转移**的情况只需额外付出多项式阶的学习代价，不影响上述定性结论。
4. **实际意义**：若反馈仅为二元信号（例如人工评分短片段），划分更多片段能极大加速学习；若可得到精确的累积和反馈，则没必要划分太细，因为收益微乎其微。

## 7. 优点
- **理论深度**：首次严格刻画了分段粒度对学习性能的指数影响（二进制）和几乎无影响（求和），并给出了匹配的下界。
- **算法新颖**：在二进制反馈中采用 Thompson 采样，避免了之前工作（Chatterji et al.）的非马尔可夫性或 $O(K^{2/3})$ 遗憾；在求和反馈中利用 E-最优实验设计改进了已有轨迹反馈结果一个 $\sqrt{H}$ 因子。
- **桥接模型**：提出的片段反馈模型统一了每步奖励、轨迹奖励两端，为未来更一般的不等长分段、函数近似扩展奠定了理论基础。
- **分析技巧**：在二进制下利用 KL 散度与 sigmoid 导数的关系导出指数下界，具有独立参考价值。

## 8. 不足与局限
- **实验弱**：仅在小规模表格 MDP 上做模拟，未在任意标准 RL 基准（如 Mujoco、Atari）上验证，无法确认算法在现实任务中的实际效果。
- **计算瓶颈**：求和反馈的 E-LinUCB 算法需要求解 E-最优设计并枚举所有策略（ $\Pi = A^{|S|}$ ），在状态空间较大时不可行。作者也承认该算法主要为了揭示理论依赖关系。
- **假设限制**：假设 $H$ 可被 $m$ 整除，且片段长度相等；实际场景中分段可能不等长，论文未考虑。
- **可复现性**：论文未提供代码，核心超参数（如置信半径 $\nu(k)$ 中的常数）需仔细调整，且未讨论调参敏感性。
- **实验客观性**：缺少与已有轨迹反馈方法的直接比较，仅展示了自身算法在不同 $m$ 下的趋势，说服力有限。

（完）
