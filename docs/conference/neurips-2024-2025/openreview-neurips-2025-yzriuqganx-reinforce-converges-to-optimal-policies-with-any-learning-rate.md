---
title: REINFORCE Converges to Optimal Policies with Any Learning Rate
title_zh: 任意学习率下REINFORCE收敛到最优策略
authors: "Samuel McLaughlin Robertson, Thang D. Chu, Bo Dai, Dale Schuurmans, Csaba Szepesvari, Jincheng Mei"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=YzriuQGaNX"
tags: ["query:graph-part"]
score: 9.0
evidence: REINFORCE策略梯度收敛性理论证明
tldr: 该文证明了经典的REINFORCE随机策略梯度方法在有限时域马尔可夫决策过程中，使用任意常值学习率都能收敛到全局最优策略。文中首先在随机赌博机设置中证明了无限探索性质，随后将其推广至MDP。理论分析表明REINFORCE本身具备渐进探索能力，无需依赖假设。该工作奠定了策略梯度方法收敛性的坚实基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1371, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1353, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1434, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1363, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1131, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1131, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1128, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1130, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 977, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1132, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yzriuqganx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1130, \"height\": 648, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-yzriuqganx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 807, \"height\": 388, \"label\": \"Table\"}]"
motivation: 经典REINFORCE算法的收敛性仅在小学习率或衰减学习率下已知。
method: 通过证明在线法无穷动作采样性质，消除了对学习率衰减的需求。
result: 证明任意学习率下REINFORCE收敛到全局最优。
conclusion: 为策略梯度方法的收敛性提供了更普适的理论保证。
---

## Abstract
We prove that the classic REINFORCE stochastic policy gradient (SPG) method converges to globally optimal policies in finite-horizon Markov Decision Processes (MDPs) with $\textit{any}$ constant learning rate. To avoid the need for small or decaying learning rates, we introduce two key innovations in the stochastic bandit setting, which we then extend to MDPs. $\textbf{First}$, we identify a new exploration property of SPG: the online SPG method samples every action infinitely often (i.o.), improving on previous results that only guaranteed at least two actions would be sampled i.o. This means SPG inherently achieves asymptotic exploration without modification. $\textbf{Second}$, we eliminate the assumption of unique mean reward values, a condition that previous convergence analyses in the bandit setting relied on, but that does not translate to MDPs. Our results deepen the theoretical understanding of SPG in both bandit problems and MDPs, with a focus on how it handles the exploration-exploitation trade-off when standard optimization and stochastic approximation methods cannot be applied, as is the case with large constant learning rates.

---

## 论文详细总结（自动生成）

# 论文总结：REINFORCE Converges to Optimal Policies with Any Learning Rate

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：传统的REINFORCE算法（随机策略梯度方法）在随机设置中的理论收敛性证明通常要求学习率足够小或采用衰减学习率，这与实际应用中常用的大常数学习率不符。现有工作（如Mei et al., 2024b; Klein et al., 2024）虽然给出了常数学习率下的收敛保证，但学习率必须非常小（依赖于未知的奖励间隙），或者依赖于“无平局奖励”的强假设（Assumption 3.1），该假设在赌徒臂（bandit）设置中已经难以验证，更无法推广到马尔可夫决策过程（MDP）——因为在MDP中，即使立即奖励不同，多条最优轨迹仍然存在（例如图1中的树形MDP）。
- **核心问题**：希望证明REINFORCE在任意常数学习率下都能几乎必然收敛到全局最优策略，并消除对“奖励无平局”假设的依赖。同时揭示算法内在的探索特性，解释为什么即使存在多个最优解，策略仍能收敛到最优动作集（但不一定收敛到单一的最优动作）。
- **整体含义**：该工作首次在随机设置中给出了REINFORCE使用任意常值学习率下的全局收敛证明，弥合了理论与实践之间的差距，加深了对随机策略梯度方法探索-利用平衡机制的理解。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：
  - 在赌徒机（bandit）设置中，证明随机梯度赌徒算法（Algorithm 1）具有**全臂无限探索**性质（Lemma 4.1）：每个动作都会被无限次采样，这打破了之前仅保证至少两个动作被无限采样的结论。
  - 利用该探索性质，进一步证明即使存在奖励平局，算法也能收敛到最优动作集（Theorem 4.2）。关键步骤是：证明最优参数之和发散到正无穷（Proposition 4.3），而每个次优参数发散到负无穷（Proposition 4.4）。
  - 将赌徒机结果扩展到**非平稳赌徒机设置**（Section 5.1），其中奖励均值随时间漂移但最终稳定在真实均值附近（偏差 ≤ Δ/3）。然后通过**反向归纳法**将此结果应用于有限时域MDP：从最后的时步开始，逐步向前证明每个状态的最优动作选择概率趋于1（Theorem 5.2）。核心是利用前一阶段已经近似最优，从而后一阶段的Q值差距在足够大后稳定，进而应用非平稳赌徒机收敛结果。

- **关键技术细节**：
  - **探索引理（Lemma 4.1）**：证明过程通过反证法，利用Extended Borel-Cantelli引理和Freedman不等式（Lemma A.3），分析参数演化。关键步骤：假设存在动作a被有限次采样，则其参数有界且概率趋于0；而此时必有另一动作b被无限采样且参数反复跌至很低再弹回，导致“θt(b) ≤ θt(a)且at=b”的事件无限发生，但该事件的条件概率受限于πt(a) → 0，矛盾。
  - **收敛证明**：
    - 对于最优动作集A*，定义增量Xt = Σ_{a∈A*} [θt+1(a)-θt(a)]，证明其条件期望下界为ηπt(A*)(1-πt(A*))Δ，条件方差上界为η²R²πt(A*)(1-πt(A*))，满足方差与期望成比例，结合无限探索保证期望和发散，从而应用Freedman发散技巧得到最优参数和→∞。
    - 对于次优动作集，通过归纳分组（按期望奖励分层），利用条件期望的负上界和Freedman不等式证明每个次优动作参数→ -∞。
  - **RL中的反向归纳**：假设在后续时步h',...,H-1所有状态的最优动作概率→1，则在时步h-1的Q值差距最终大于Δ/3，而REINFORCE在该状态的更新等价于一个非平稳赌徒机（因为后续回报随策略变化，但最终稳定），应用非平稳赌徒机收敛定理即得。
  - **算法流程**：标准REINFORCE（Algorithm 2）：每轮采样一个完整轨迹，利用REINFORCE估计量更新每个状态-动作对的参数θ(s,a)。参数更新公式为：θt+1(s,a) = θt(s,a) + η * (∑_{h'=h}^{H-1} r_{h'}) * (I[a_h=a]-π_t(a|s))。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **场景**：
  - **链式MDP（Chain MDP）**：图1b所示，状态s0-s3，终端T1/T2。动作a0一步到终端得+0.5；动作a1向左下步进（-0.5），但最终在s3取a1得+7到T2。这是一个有长短期回报权衡的问题，存在唯一最优路径（全程选a1）。用于测试学习率大小对收敛速度的影响。
  - **树形MDP（Tree MDP）**：图1a所示，多条最优轨迹（s1→s2→s5和s1→s3→s8总报酬均为3），用于演示策略非平稳收敛现象（Proposition 3.2）。
  - **DeepSea环境**：方形网格世界，深度d=5,6,7，起点左上角，终点右下角。动作1向下，动作2向下右（惩罚）。用于测试不同复杂度下的学习率-性能“碗形”关系。
  - **CartPole环境**：经典控制任务，用于验证大规模学习率下REINFORCE的性能（仅测试几个学习率：1e-5, 1e-4, 1e-2, 1）。

- **Benchmark和对比方法**：没有与其他算法（如PPO、TRPO等）进行对比，主要是自我比较不同学习率下的表现，以及验证理论预测的现象（如反向收敛模式）。baseline是理论推导的收敛保证，实验起到验证作用。

- **对比方法**：未使用，仅测试REINFORCE自身在不同学习率和环境下的行为。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等算力资源。所有实验均在简单MDP（最多几个状态）和经典控制环境中进行，可以推断在普通CPU/笔记本电脑上即可完成。作者提到“ChainMDP和TreeMDP足够简单，可在任何现代机器上运行（例如2019年Intel Macbook）”。
- 值得注意的是，DeepSea深度最大仅为7，CartPole也仅训练10⁵个episode，算力需求很低。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要实验：ChainMDP（H=4,5,6）测试了100个不同学习率（从e⁻⁹到e¹⁰之间的对数间隔），每个学习率30个随机种子，共约3000次运行。
  - DeepSea（深度5,6,7）：同样测试100个学习率，每个30个种子。
  - CartPole：仅测试4个学习率，5个种子。
  - 另外有展示非平稳收敛现象的树形MDP实验（单次运行示例，未显示误差棒）。
- **充分性**：
  - 对于Chain和DeepSea，覆盖了广泛的学习率范围，并报告了平均次优性差距随学习率变化的“碗形”曲线，结果清晰表明过大或过小的学习率都会导致性能下降，而中等学习率表现最佳。这与理论分析（任意学习率下渐近收敛，但过大学习率方差大收敛慢）一致。
  - 实验设计客观：每次用相同参数初始化（θ=0），不同种子保证统计可靠性，使用阴影表示标准差。
  - 不足之处：实验规模较小（最大深度7、最多10⁵回合），未在更大规模（如Atari游戏）或深度神经网络策略上验证。此外，没有与其他策略梯度变体（如PPO、A2C）进行比较，因此不能直接说明REINFORCE比它们更好或更差。实验主要是为了验证理论结论，而非提出新算法。

## 6. 论文的主要结论与发现

- **发现1**：随机梯度赌徒算法（Algorithm 1）具有**全臂无限探索**性质，即每个动作都会被无限次采样（Lemma 4.1）。这一性质不依赖于学习率大小，也不需要任何显式的探索机制。
- **发现2**：在传统赌徒机设置中，即使存在奖励平局（多个动作均值相同），算法仍能收敛到最优动作集（Theorem 4.2）。Pi_t(A*) → 1 a.s.。但策略参数本身不会收敛到单一的独热向量，而是在最优动作之间振荡（Proposition 3.2）。
- **发现3**：将赌徒机结果推广到非平稳赌徒机，进而通过反向归纳证明REINFORCE在有限时域MDP中，使用任意常数学习率时，几乎必然收敛到全局最优策略（Theorem 5.2）。具体表现为每个状态的最优动作概率趋于1。
- **发现4**：实验表明，存在一个最优学习率范围，过小（收敛过慢）或过大（方差大、收敛震荡）都会降低性能，形成碗形关系。大学习率虽能渐近收敛，但实际收敛速度可能不如中等学习率。

## 7. 优点：方法或实验设计上的亮点

- **理论贡献突出**：
  - 首次证明REINFORCE在任意常值学习率下的全局收敛，消除了对特殊学习率调度或唯一最优解假设的依赖。
  - 揭示了随机梯度方法的内在探索能力（全臂无限采样），这是非常强的性质，且证明不依赖于渐进分析中常见的平滑性或凸性假设，纯粹基于随机过程的鞅和Freedman不等式。
  - 通过反向归纳将赌徒机结果延伸到MDP，不仅解决了零奖励间隙问题，还提供了一种可推广的证明框架。
- **实验设计合理**：
  - 使用简单但具有代表性的MDP（链型、树型、DeepSea）清晰地展示了理论预测的现象：反向收敛顺序、学习率-性能曲线。
  - 对多个学习率进行系统扫描，并报告统计量（平均±标准差），结果稳健。
  - 提供了定性地验证了“非平稳收敛”现象（Proposition 3.2）的模拟，增加了理论的可信度。

## 8. 不足与局限

- **实验覆盖有限**：
  - 仅在表格型、小规模MDP上验证，未在连续状态/动作空间或深度神经网络策略上测试。理论本身限定于表格型softmax参数化和有限状态动作空间，因此实验范围与理论匹配，但缺乏对实际应用场景的参考。
  - 没有与其他先进的策略梯度算法（如PPO、TRPO、A2C）对比，无法说明REINFORCE在实践中的竞争力。
  - 假设奖励有界（[-R,R]）、转移概率固定、有限时域，这些假设在实际问题中可能不成立（如无限时域或奖励无界）。
- **收敛率分析较弱**：
  - 虽然给出了收敛速率为O(log T / T)，但这是平均次优性，且依赖于经验参数（如τ需要足够大）。常数常数可能很大，实际应用参考价值有限。
  - 没有给出首次到达ε-最优的策略复杂度的具体界。
- **对“任意学习率”的解读**：
  - 理论证明适用于任何正数η，但实验显示过大η会导致高方差和慢收敛。因此实际使用时仍然需要调节学习率，并非“任意学习率都好”。
- **非平稳赌徒机的假设**：
  - 假设存在一个固定真实均值r，且最终漂移偏差<Δ/3。这仍然需要预先知道最小非零间隙Δ，实际上可能未知。
- **缺少消融实验**：
  - 没有系统地验证“全臂无限探索”性质是否在更复杂环境中仍然成立（例如使用函数逼近时）。理论仅针对表格设置。

（完）
