---
title: "Reinforcement Learning Under Latent Dynamics: Toward Statistical and Algorithmic Modularity"
title_zh: 潜动力学下的强化学习：迈向统计与算法模块化
authors: "Philip Amortila, Dylan J Foster, Nan Jiang, Akshay Krishnamurthy, Zakaria Mhammedi"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=qf2uZAdy1N"
tags: ["query:graph-part"]
score: 6.0
evidence: 潜动力学下的强化学习统计与算法模块性研究
tldr: 本文研究了通用潜动力学下的强化学习统计与算法挑战，主要负结果表明在函数近似下大多数经典RL设定变得不可解。算法方面提出模块化设计，尝试分解观测与动力学学习。该工作为理解复杂观测下RL的基本困难提供了理论指导。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-qf2uzady1n/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 973, \"height\": 780, \"label\": \"Table\"}]"
motivation: 实际RL中观测复杂但动力学简单，现有理论难以扩展到通用潜动力学。
method: 从统计和算法双视角分析潜动力学RL，给出负结果并探索模块化分解方法。
result: 证明函数近似下大多数经典RL设定在潜动力学下不可解，揭示了根本困难。
conclusion: 该工作为潜动力学RL提供了理论基础和模块化设计方向。
---

## Abstract
Real-world applications of reinforcement learning often involve  environments where agents operate on complex, high-dimensional observations, but the underlying (``latent'')  dynamics are comparatively simple. However, beyond restrictive settings
  such as tabular latent dynamics,  the fundamental statistical requirements and algorithmic principles for *reinforcement learning under latent dynamics* are poorly
  understood.

  This paper addresses the question of reinforcement learning under *general latent dynamics* from a
  statistical and algorithmic perspective.  On the statistical side, our main negative
result shows that *most* well-studied settings for reinforcement learning with function approximation become intractable when composed with rich observations; we complement this with a positive result, identifying *latent pushforward coverability* as a
general condition that enables statistical tractability. Algorithmically, we develop provably efficient *observable-to-latent* reductions ---that is, reductions that transform an arbitrary algorithm for the
  latent MDP into an algorithm that can operate on rich observations--- in two settings: one where the agent has access to hindsight
observations of the latent dynamics (Lee et al., 2023) and one
where the agent can estimate *self-predictive* latent models (Schwarzer et al., 2020). Together, our results serve as a
  first step toward a unified statistical and algorithmic theory for
reinforcement learning under latent dynamics.

---

## 论文详细总结（自动生成）

# 中文总结：Reinforcement Learning under Latent Dynamics

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现实世界中的强化学习（RL）应用通常涉及复杂、高维的观测（如图像、文本），但环境的底层动力学却相对简单（低维潜在状态空间）。经典RL理论通常假设直接观测状态，而实际中需要在复杂观测下进行决策。现有理论工作大多局限于特定假设（如表格型潜在状态、线性动力学等），缺乏对通用潜动力学的理解。
- **核心问题**：如何从统计和算法两个角度理解“潜动力学下的RL”？具体包括：
  - 统计模块化：如果一个基类MDP在直接观测下是可学习的，那么对应的潜动力学问题是否仍然可学习？是否有统一的统计复杂度刻画？
  - 算法模块化：能否将已有的潜状态空间RL算法通过表示学习“提升”到观测空间，实现模块化约简？
- **整体贡献**：本文首次系统研究了通用潜动力学的RL，给出了否定结果（大多数函数近似设定不可扩展）和肯定结果（推前覆盖性保证可学习性），并提出了两种观测到潜状态的约简方法（后见可观测性和自预测表示学习），为统一理论奠定了基础。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（文字说明）

### 2.1 框架定义
- **潜动力学MDP**：由一个基MDP（潜状态空间S、动作空间A、转移和奖励）和一个可解码的发射过程ψ（将潜状态映射到观测分布）构成。发射过程满足可解码性：不同潜状态对应的观测支撑集不相交，从而存在解码器ϕ = ψ⁻¹。
- **潜动力学MDP类**：给定基MDP类Mlat和编码器类Φ，定义⟪Mlat, Φ⟫为所有由Mlat∈Mlat和可解码发射过程（其解码器∈Φ）诱导的观测空间MDP。

### 2.2 统计模块化：否定结果与肯定结果
- **统计模块化定义**：若基类Mlat的统计复杂度（样本复杂度）为comp(Mlat, ε, δ)，则对任意解码器类Φ，潜动力学类⟪Mlat, Φ⟫的样本复杂度是comp(Mlat, ε, δ)和log|Φ|的多项式函数。
- **否定结果（Theorem 3.1）**：即使基MDP已知（|Mlat|=1），只要解码器类规模N足够大，学习潜动力学MDP至少需要Ω(N/log N)轮交互。该构造基于一个二叉树型MDP，解码器类为循环置换。因此，大多数函数近似设定（线性MDP、贝尔曼秩、埃尔伍德维数等）不具有统计模块化性质。
- **肯定结果（Theorem 3.2）**：推前覆盖性（pushforward coverability）是保证统计模块化的充分条件。若每个基MDP的推前覆盖系数Cpush有界，则潜动力学类的样本复杂度为poly(Cpush, |A|, H, log|Mlat|, log|Φ|, ε⁻¹, log δ⁻¹, log log|S|)。证明思路：构造低维线性特征来近似贝尔曼备份，从而满足GOLF算法的贝尔曼完备性假设。

### 2.3 算法模块化：两种可观测到潜状态的约简
- **O2L元算法（Algorithm 1）**：交替进行表示学习和基算法执行。每轮t，表示学习器REP_LEARN输出一个解码器ϕ̂⁽ᵗ⁾；然后基算法ALG_lat在压缩数据（将观测通过ϕ̂⁽ᵗ⁾映射到潜状态）上运行K轮，最后输出策略π̂ₗₐₜ；最终策略为均匀混合所有轮次的π̂ₗₐₜ ∘ ϕ̂⁽ᵗ⁾。
- **后见可观测性（Theorem 4.1）**：假设训练时每轮结束后能观察到真实潜状态（但部署时不行）。通过在线分类算法（如指数权重去随机化）实现表示学习。风险界：E[Risk_obs(TK)] ≤ Risk*(K) + (2K/T) Est_class(T)。其中Risk*(K)是基算法在真实潜状态上的期望风险，Est_class(T)是分类遗憾。实例化后得到O(H log|Φ|/ε⁵)的样本复杂度。
- **自预测估计（Theorem A.1）**：无需后见观测，通过联合学习解码器和潜模型的最小化自预测误差。定义乐观自预测遗憾：Reg_self;opt(T,γ) = 累计Hellinger距离 + γ⁻¹(J(π*) - J(ĉM))。核心是设计一个“去偏”最大似然估计器（SELF_PREDICT_OPT），在可覆盖性和不匹配完备性假设下达到Õ(√(H C_cov|A|T log(|Mlat||Llat||Φ|)))的遗憾。总风险界为：E[Risk_obs(TK)] ≤ c1·Risk_base(K) + c2γ·K/T·Est_self;opt(T,γ) + c3γ⁻¹·KH。

## 3. 实验设计

- **本文为纯理论论文，没有进行任何实验或仿真**。所有结论均基于数学证明和理论分析，不涉及数据集、基准方法或实际环境测试。

## 4. 资源与算力

- **未提及任何计算资源**。由于无实验，无需GPU或大规模算力。

## 5. 实验数量与充分性

- **不适用**。无实验设计，因此无法评价实验的充分性或公平性。

## 6. 论文的主要结论与发现

- **统计模块化不可扩展**：大多数流行的函数近似RL设定（贝尔曼秩、埃尔伍德维数+贝尔曼完备性、线性Q*/V*、线性混合MDP等）在潜动力学下变得统计上不可学习（即使基MDP已知）。
- **推前覆盖性可保证可学习性**：如果基MDP类满足推前覆盖性，则潜动力学问题可学习，复杂度多项式和类规模与解码器规模对数相关。
- **后见可观测性下的通用约简**：只需在线分类遗憾小，即可将任意基RL算法提升到观测空间，无额外结构假设。
- **自预测表示学习实现无后见约简**：通过乐观自预测目标，在可覆盖性和不匹配完备性假设下，同样可实现模块化约简，但复杂度略高。
- **提供理论依据**：为自预测表示学习的有效性提供了理论支撑，揭示了其与乐观估计的结合机制。

## 7. 优点

- **框架统一**：首次提出“潜动力学RL”的通用框架，超越了表格、线性等特殊情形。
- **全面分类**：系统总结了多种基MDP类的统计模块化性质（图1），并给出证明。
- **算法模块化设计**：O2L元算法简单通用，可搭配任意基算法和表示学习器，实现“即插即用”。
- **自预测理论的严谨处理**：解决了自预测估计中的双重采样、非马尔可夫性、乐观性等关键问题，给出了首个通用保证。
- **理论深度**：证明技术包括随机嵌入（JL引理）、去偏MLE、在线到离线转换等，具有技巧性。

## 8. 不足与局限

- **缺乏计算效率**：自预测估计器SELF_PREDICT_OPT基于经验风险最小化，未考虑计算可行性（复杂度可能很高），论文明确指出这是开放问题。
- **强假设**：不匹配完备性假设（Assumption A.2）和可覆盖性假设在一般场景下难以满足；解码器类Φ的规模可能很大，影响实际应用。
- **仅限可解码发射过程**：要求潜状态可从观测唯一解码（Block MDP风格），不适用于部分可观测的一般POMDP。
- **未实验验证**：理论结果未配套仿真或基准测试，其实用性需进一步验证。
- **乐观自预测目标**：需要优化项γ⁻¹(J(π*) - J(ĉM))，在计算上不易实现，且γ选择依赖未知量。

（完）
