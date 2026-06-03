---
title: Provably Efficient Partially Observable Risk-sensitive Reinforcement Learning with Hindsight Observation
title_zh: 具有后见观察的部分可观察风险敏感强化学习的可证明高效性
authors: "Tonghe Zhang, Yu Chen, Longbo Huang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=5S8ukkEQr2"
tags: ["query:graph-part"]
score: 8.0
evidence: 部分可观察风险敏感RL的可证明高效算法，利用后见观察
tldr: "该论文首次研究了具有后见观察的部分可观察风险敏感强化学习问题，提出了一个可证明高效的学习算法。算法在熵风险度量下优化累积奖励，并证明了多项式遗憾界tilde{O}(e^{|gamma|H}-1)/|gamma|H H^2 sqrt{KHS^2OA})，突破现有理论空白。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-5s8ukkeqr2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5s8ukkeqr2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 802, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5s8ukkeqr2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 889, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-5s8ukkeqr2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1771, \"height\": 787, \"label\": \"Figure\"}]"
motivation: 风险敏感RL在部分可观察环境中的理论分析缺失，特别是在结合后见观察时。
method: 将后见观察集成到POMDP框架中，设计了一种新的RL算法，结合风险度量和后见信息。
result: 算法获得多项式遗憾界，在退化模型下优于或匹配现有上界。
conclusion: 填补了部分可观察风险敏感RL的理论空白，提供了首个可证明高效的算法。
---

## Abstract
This work pioneers regret analysis of risk-sensitive reinforcement learning in partially observable environments with hindsight observation, addressing a gap in theoretical exploration. We introduce a novel formulation that integrates hindsight observations into a Partially Observable Markov Decision Process (POMDP) framework, where the goal is to optimize accumulated reward under the entropic risk measure. We develop the first provably efficient RL algorithm tailored for this setting. We also prove by rigorous analysis that our algorithm achieves polynomial regret $\tilde{O}\left(\frac{e^{|{\gamma}|H}-1}{|{\gamma}|H}H^2\sqrt{KHS^2OA}\right)$, which outperforms or matches existing upper bounds when the model degenerates to risk-neutral or fully observable settings. We adopt the method of change-of-measure and develop a novel analytical tool of beta vectors to streamline mathematical derivations. These techniques are of particular interest to the theoretical study of reinforcement learning.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在实际决策中（如自动驾驶、股票交易、网络安全），决策者常面临部分可观察环境（POMDP），同时需要控制风险。现有风险敏感强化学习（RL）研究主要集中于完全可观察的MDP，或仅关注POMDP下的规划问题（假设模型已知），缺乏对**部分可观察环境下风险敏感RL样本复杂度**的理论分析。  
- **背景**：一般POMDP的学习已被证明是计算难解的，但“后见观察”（hindsight observation）——即在每幕结束后回顾隐藏状态——使得样本高效学习成为可能。本文首次将**后见观察**与**熵风险度量**结合，填补了部分可观察风险敏感RL的理论空白，提出第一个可证明高效的算法。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：将后见观察集成到POMDP框架中，利用测度变换（change-of-measure）技术将原模型转化为参考模型（参考模型中观察与状态独立），从而简化值函数的Bellman方程。引入**风险信念**（risk belief）和**β向量**（beta vector）来捕获累积风险并线性化值函数，进而设计探索奖励函数。
- **关键技术细节**：
  - **模型设定**：考虑非平稳的表格型POMDP，每个步骤的状态、观察、动作空间有限；目标最大化熵风险度量 \( J(\pi;P,\gamma) = \frac{1}{\gamma}\ln\mathbb{E}^\pi_P\left[e^{\gamma\sum_{t=1}^H r_t}\right] \)。
  - **测度变换**：定义参考模型 \(P'\)，其中观察独立于状态（均匀分布），原期望可通过Radon-Nikodym导数转换。
  - **风险信念** \(\sigma_{h,f_h}\)：记录给定历史下各隐藏状态的累积风险，更新规则为矩阵乘法。
  - **β向量** \(\beta_{h,f_h}\)：表示值函数与风险信念的内积 \(V_h(f_h)=\frac{1}{\gamma}\ln\langle\sigma_{h,f_h},\beta_{h,f_h}\rangle\)，具有类似于α向量的马尔可夫性，使得规划复杂度不依赖于历史空间大小。
  - **奖励函数**：基于偏差分析和浓度不等式设计，形式为  
    \[
    b_h^k(s_h,a_h) = (e^{\gamma(H-h+1)}-1)\cdot\min\{1,\; t_h^k(s_h,a_h)+\sum_{s'} \hat{T}_{h,a_h}^k(s'|s_h) o_{h+1}^k(s')\}
    \]
    其中 \(t_h^k,o_{h+1}^k\) 分别控制转移和发射误差的浓度界。
  - **算法流程**（BVVI，Beta Vector Value Iteration）：
    1. 每幕开始，基于当前经验模型初始化风险信念。
    2. 对每个步骤 \(h\)，**前向传播**更新风险信念，并计算探索奖励。
    3. **后向规划**：从H+1至1，利用β向量及奖励函数计算Q值、值函数和贪婪策略，同时裁剪β向量以控制范围。
    4. **学习**：在真实环境中执行策略，收集轨迹，幕末通过后见观察获得隐藏状态，更新经验模型。
- **关键公式**：Bellman最优方程（式(50)）、β向量更新式（55）、遗憾上界（式(79)）。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **实验场景**：作者构建了一个小型POMDP（\(S=3, O=3, A=2, H=4\)），转移和观察概率随机设定；同时构造了一个MDP（将POMDP的发射矩阵改为单位阵）作为完全可观察的对比。
- **基准（benchmark）**：由于该问题是首次被提出，没有现成的基线算法。作者主要与**自身理论预测**（theoretical regret曲线）进行比较，并验证了风险敏感参数γ变化时算法的行为。
- **对比方法**：未与其他算法直接对比；而是比较了**MDP vs POMDP**环境下BVVI的累积遗憾，以及**不同γ值**下的性能。因此是自我验证性实验。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- **未说明**：论文中没有提及使用的GPU型号、数量或训练时长。由于是表格型试验且环境规模很小（\(K=2000\)幕），可能仅在CPU上即可完成，无需大量算力。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平

- **实验数量**：两组主要实验：
  1. **MDP vs POMDP**：在相同风险参数 \(\gamma=1\) 下，比较累积遗憾和每幕回报（Figure 1和Figure 3）。
  2. **不同风险敏感参数**：在POMDP中取 \(\gamma \in \{-5,-3,-1,1,3,5\}\)，比较累积遗憾和最优性差距（Figure 2和Figure 4）。
- **充分性与公平性**：
  - **优点**：实验覆盖了正负γ值，且展示了亚线性遗憾，验证了理论；POMDP和MDP的对比显示了部分观察带来的额外困难。
  - **不足**：
    - 仅有单个随机生成的POMDP实例，未在不同随机种子、不同状态/观察空间规模下重复实验。
    - 没有与其他风险敏感POMDP算法（如基于粒子滤波或近似方法的基线）对比，因为此类工作多缺少理论保证且未公开实现。
    - 未进行消融研究（如移除探索奖励、不使用后见观察等）来验证各组件有效性。
  - **客观性**：实验代码未公开，但结果与理论遗憾界趋势一致（约 \(\tilde{O}(\sqrt{K})\)），具备一定合理性。

### 6. 论文的主要结论与发现

1. **首次提供了部分可观察风险敏感RL的遗憾分析**，在结合后见观察和熵风险度量框架下，提出BVVI算法并证明其遗憾界为  
   \(\tilde{O}\left(\frac{e^{|γ|H}-1}{|γ|H} H^2 \sqrt{K S^2 A O} \cdot \sqrt{H \ln\frac{KHSOA}{δ}}\right)\)。  
2. **退化性质**：当γ→0（风险中性）时，遗憾界改进并匹配或优于现有HOMDP算法（Lee et al., 2023）；在完全可观察MDP下，经过适配后得到与Fei et al.（2021a）相同的上界，并接近信息论下界。  
3. **技术贡献**：提出了β向量工具，简化了值函数表示和探索奖励设计；采用测度变换解耦状态与观察，简化了分析。

### 7. 优点：方法或实验设计上有哪些亮点

- **理论突破**：首次将风险敏感RL与部分可观察性问题结合，并给出多项式遗憾界，填补了长期存在的理论空白。
- **技术新颖性**：
  - β向量的提出使得值函数可表示为风险信念与β向量的内积，从而在非线性的风险度量下仍保持类似α向量的马尔可夫性质，避免了历史维度爆炸。
  - 探索奖励设计考虑了转移和发射误差的浓度界，同时通过裁剪确保β向量范围可控。
- **泛化性**：多数结果可扩展到一般效用风险度量（如CVaR等），附录B中给出了推导。
- **实验简洁有效**：虽然实验规模小，但直观展示了算法在MDP和POMDP下的亚线性遗憾，并与理论趋势吻合，验证了核心结论。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖有限**：仅在单一小型POMDP上进行测试，未在更大规模（如\(S,O>10\)）或真实场景（如机器人控制、金融）中评估，实际性能未知。
- **缺乏基线对比**：由于问题新颖且现有算法缺少理论保证，未与任何近似方法（如PPO+RNN+风险截断等）对比，无法体现算法相对实际启发式方法的优势。
- **计算复杂度**：BVVI在规划阶段需遍历整个历史域（\(\mathcal{F}_h\)），导致计算量随H指数增长（尽管样本复杂度是多项式）。文中承认了这一局限，并提出可使用点规划近似，但未实验验证。
- **对后见观察的依赖**：算法要求每幕结束后获知隐藏状态，这在许多真实场景中不可行，限制了应用范围。
- **风险度量局限**：仅分析熵风险（以及一般效用风险），未涵盖CVaR、动态风险等更常用风险度量，泛化能力有待证明。
- **遗憾界简化**：最终上界省略了低阶项（如与\(\sqrt{K}\)相比更低阶的项），实际常数可能较大。

（完）
