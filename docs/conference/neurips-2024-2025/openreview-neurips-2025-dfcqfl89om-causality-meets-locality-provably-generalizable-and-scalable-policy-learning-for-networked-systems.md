---
title: "Causality Meets Locality: Provably Generalizable and Scalable Policy Learning for Networked Systems"
title_zh: 因果性与局部性：面向网络系统的可泛化可扩展策略学习
authors: "Hao Liang, Shuqing Shi, Yudi Zhang, Biwei Huang, Yali Du"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dfcQFL89OM"
tags: ["query:graph-part"]
score: 6.0
evidence: 针对大规模网络系统的可扩展和可泛化强化学习方法
tldr: 在大规模网络系统（如交通、电力、无线网络）中，强化学习面临可扩展性和环境迁移挑战。本文提出GSAC框架，将因果表示学习与元actor-critic学习相结合，每个智能体学习稀疏局部因果掩码以识别最小邻域变量，得到紧致的近似压缩表示，从而截断值函数误差有界。理论证明了表示的可泛化性，实验验证了在多个网络系统任务上的性能提升。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 450, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1214, \"height\": 846, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1397, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1328, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1357, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1409, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1408, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfcqfl89om/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1408, \"height\": 442, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfcqfl89om/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1397, \"height\": 2260, \"label\": \"Table\"}]"
motivation: 大规模网络系统对强化学习智能体的可扩展性和环境迁移能力提出挑战。
method: 结合因果表示学习与元actor-critic，学习局部因果掩码以获取近似紧致的状态表示。
result: 理论证明表示可泛化且误差有界，实验显示在多种网络场景下性能优于基线。
conclusion: 局部因果掩码是实现网络系统RL可扩展和可泛化的有效途径。
---

## Abstract
Large‑scale networked systems, such as traffic, power, and wireless grids, challenge reinforcement‑learning agents with both scale and environment shifts. To address these challenges, we propose \texttt{GSAC} (\textbf{G}eneralizable and \textbf{S}calable \textbf{A}ctor‑\textbf{C}ritic), a framework that couples  causal representation learning with meta actor‑critic learning to achieve both scalability and domain generalization. Each agent first learns a sparse local causal mask that provably identifies the minimal neighborhood variables influencing its dynamics, yielding exponentially tight approximately compact representations (ACRs) of state and domain factors. These ACRs bound the error of truncating value functions to $\kappa$-hop neighborhoods, enabling efficient learning on graphs. A meta actor‑critic then trains a shared policy across multiple source domains while conditioning on the compact domain factors; at test time, a few trajectories suffice to estimate the new domain factor and deploy the adapted policy. We establish finite‑sample guarantees on causal recovery, actor-critic convergence, and adaptation gap, and show that \texttt{GSAC} adapts rapidly and significantly outperforms learning-from-scratch and conventional adaptation baselines.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文内容，以下是对该论文《Causality Meets Locality: Provably Generalizable and Scalable Policy Learning for Networked Systems》的详细中文总结。

# 中文总结

## 1. 核心问题与整体含义

- **研究动机与背景**：大规模网络系统（如交通网络、电力网络、无线通信系统）中的强化学习（RL）面临两大根本性挑战：**可扩展性**和**泛化性**。一方面，联合状态-动作空间随智能体数量指数增长，传统RL算法计算上不可行；另一方面，真实网络系统常经历环境变化和结构变动，要求算法能在不同环境间有效泛化和适应。
- **核心问题**：是否可能为网络系统设计一个可证明具有泛化能力和可扩展性的多智能体强化学习（MARL）算法？
- **整体含义**：本文给出了肯定答案，提出因果启发框架**GSAC**（Generalizable and Scalable Actor-Critic），通过将**因果表示学习**与**元Actor-Critic学习**相结合，同时实现了可扩展性和域泛化能力，并提供了理论保证。

## 2. 方法论

- **核心思想**：利用网络系统中智能体交互的局部性（邻居依赖）和因果结构，识别影响每个智能体动态的最小邻域变量集合（称为近似紧致表示，ACR），从而显著降低状态和域因子输入维度。在此基础上，采用元学习方法在多个源域上训练一个共享的域条件策略，在新目标域中仅需少量轨迹即可估计域因子并直接部署适应后的策略。
- **关键技术细节**：
  - **因果掩码恢复与域因子估计**：假设每个智能体的局部转移动态由共享的因果结构（二进制掩码）和可变的潜在域因子决定。在标准忠实性假设下，**定理1**保证了因果掩码的可辨识性；**命题4**和**命题5**分别给出了因果掩码恢复和域因子估计的有限样本复杂度（准线性于输入维度，随因果信号强度二次衰减，对于域因子估计误差为O(1/√Te)）。
  - **近似紧致表示（ACR）构造**：
    - **值函数ACR**：递归定义κ跳邻域内影响智能体奖励的最小状态变量子集，基于此的紧凑Q函数近似误差随κ指数衰减（**命题1**，界为2¯r/(1-γ)·γ^(κ+1)）。
    - **策略ACR**：类似地构造局部策略输入的最小变量子集，聚合物策略的近似误差同样指数衰减（**命题2**，界为3¯r/(1-γ)·γ^(κ+1)）。
    - **域因子ACR**：进一步将ACR扩展到域因子，用于跨域泛化，保证完全紧凑表示下近似误差有界（**命题3**，同前）。
  - **元Actor-Critic算法**：
    - **算法1**：分为四个阶段：① 因果发现与域因子估计；② ACR构造；③ 在M个源域上通过局部Actor-Critic优化元策略（Critic用TD更新，Actor用随机梯度上升）；④ 在新目标域快速适应：收集少量轨迹估计域因子后直接部署策略。
    - **理论保证**：
      - **定理2（Critic误差界）**：给定域因子估计误差，Critic估计误差由O(1/√T + 1)、指数截断误差、域因子估计误差O(√log(nTe/δ)/Te)等组成。
      - **定理3（策略梯度收敛）**：在标准假设下，策略梯度范数的平均收敛速率达到O(1/√K + ρ^(κ+1) + 1/√Te + 1/√M)。
      - **定理4（适应间隙）**：在目标域上的适应期望回报与元训练期望回报之差为O(1/√Ta)，其中Ta为适应轨迹条数。
- **优势**：ACR不仅降低了计算维度，还因减少了有效状态空间而改善了混合时间常数τ和最小访问概率σ，从而收紧收敛性常数，提升样本效率。

## 3. 实验设计

- **数据集/场景**：采用两个标准网络化MARL基准环境：
  - **无线通信（Wireless Communication）**：多个用户通过共享接入点传输数据包，每个用户维护队列，目标是最大化成功传输的奖励。用户间因共享接入点而形成交互图。域因子为数据包到达概率pi。
  - **交通控制（Traffic Control）**：由多个路口组成的路网，每个路口控制转向信号，目标是减少排队长度（负队列长度奖励）。域因子为车辆流出量C_ij的分布强度。
- **Benchmark设置**：
  - 源域：M = 3，域因子ω ∈ {0.2, 0.5, 0.8}（无线通信为pi，交通为流量强度）。
  - 目标域：ω_target = 0.65（或其他变体）。
  - 网络规模：改变网格大小（3×3, 4×4, 5×5），影响智能体数量和连接结构。
- **对比方法**：
  - **GSAC（本文）**：训练域条件策略π(a|s, ω)，测试时估计ω′并直接部署。
  - **SAC-MTL（多任务学习）**：学习π(a|s, z)，z为源域独热编码，测试时用目标域编码。
  - **SAC-FT（微调）**：不进行域条件训练，在目标域微调策略参数。
  - **SAC-LFS（从头学习）**：直接在目标域训练策略。

## 4. 资源与算力

- 论文**未明确说明**所使用的GPU型号、数量或训练时长。仅在附录中提到“limited computational budget”（有限的计算预算）。因此无法从文中获得具体算力消耗信息。

## 5. 实验数量与充分性

- **实验数量**：在无线通信基准上，进行了三个网格大小（3×3, 4×4, 5×5）的实验，并额外进行了域偏移敏感性实验（改变目标ptarget为0.6, 0.65, 0.7）。在交通控制基准上，同样进行了三个网格大小和域偏移敏感性实验。每个配置下比较了四种方法，并报告了适应初期（1-30回合）性能曲线。
- **充分性与公平性**：
  - 实验覆盖了不同网络规模和不同域偏移程度，验证了可扩展性和泛化性。
  - 对比方法合理，包括多任务、微调、从头学习等多种常见基线。
  - **不足**：论文未报告多次运行的标准差或置信区间（仅显示性能曲线趋势），未进行统计显著性检验。这削弱了结论的稳健性。此外，实验环境为表格化、完全可观测的离散空间，未扩展到连续状态/动作空间。

## 6. 主要结论与发现

- GSAC在所有测试的网格规模和域偏移条件下，均实现了**最快的适应速度**和**最高的最终回报**，显著优于SAC-LFS、SAC-FT和SAC-MTL。
- **理论结果**验证了：因果掩码可辨识、域因子估计误差随样本量以O(1/√Te)衰减，Actor-Critic收敛，适应间隙可控（O(1/√Ta)）。
- **可扩展性**：GSAC在不同网络规模（16~36个智能体）下均能有效学习，而baseline方法随规模增大性能下降更明显。
- **泛化性**：GSAC对域偏移（如目标到达概率0.6~0.7）表现鲁棒，适应后性能稳定。

## 7. 优点

- **理论完整性**：首次在networked MARL中给出因果掩码恢复和域因子估计的有限样本复杂度，并建立了从因果发现到Actor-Critic收敛再到适应间隙的完整理论链条。
- **创新方法**：提出ACR概念，将因果表示与神经网络截断技巧结合，实现了**指数级紧致的近似误差**和**实际维度大幅降低**，且这种降维能同时作用于值函数、策略和域因子。
- **算法统一**：设计了包含因果发现、ACR构造、元训练、快速适应四个阶段的端到端算法，各阶段均有理论支撑。
- **实验验证**：在两个广泛使用的网络化MARL基准上，通过变化网络规模和域因子，证明了方法在可扩展性和泛化性上的优势。

## 8. 不足与局限

- **实验覆盖不足**：
  - 仅评估了**表格化、完全可观测**的离散环境（状态和动作空间有限）。未验证在连续状态/动作空间或部分可观测条件下的表现。
  - 所有实验基于模拟器，未在真实大规模网络系统（如实际交通信号灯、无线基站）中部署。
  - 缺少对更复杂因果结构（如循环依赖、非线性）的测试。
- **统计严谨性**：
  - 未提供多次实验的标准差或置信区间，曲线可能来自单次运行，无法判断结果的稳定性。
  - 未进行消融实验来单独验证ACR、因果恢复、元学习等各组件的重要性。
- **假设限制**：理论证明依赖于若干强假设（如忠实性、子高斯噪声、有界度、Lipschitz连续性等）。在实际系统中这些假设可能不完全满足，导致理论保证减弱。
- **泛化假设**：假设域因子可以从少量轨迹中可靠估计，但实际中域因子可能难以识别或估计误差较大。
- **计算资源未报告**：缺乏对算力消耗的详细说明，不利于他人复现和评估实用性。

（完）
