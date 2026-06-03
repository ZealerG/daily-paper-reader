---
title: An Information Theoretic Approach to Interaction-Grounded Learning
title_zh: 一种信息论方法用于交互接地学习
authors: "Xiaoyan Hu, Farzan Farnia, Ho-fung Leung"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=Sra298VMFM"
tags: ["query:graph-part"]
score: 8.0
evidence: 交互接地强化学习的信息论方法
tldr: 本文针对交互接地强化学习（IGL）中潜在奖励推断问题，提出基于变分信息的VI-IGL方法，强制执行条件独立性假设，从而更准确地推断隐式奖励。实验表明该方法在IGL任务上优于现有方法，为隐式奖励学习提供了有效的信息论方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-sra298vmfm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 413, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sra298vmfm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 828, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sra298vmfm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 705, \"height\": 556, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 768, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 874, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 610, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 994, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 992, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 991, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 992, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1169, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sra298vmfm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1297, \"height\": 256, \"label\": \"Table\"}]"
motivation: IGL中需要推断未观察奖励，但条件独立性假设难以保证。
method: 提出变分信息方法VI-IGL，通过信息论约束强制执行条件独立性。
result: 实验验证了VI-IGL在IGL任务上的有效性。
conclusion: 该工作为隐式奖励推断问题提供了信息论解决方案。
---

## Abstract
Reinforcement learning (RL) problems where the learner attempts to infer an unobserved reward from some feedback variables have been studied in several recent papers. The setting of Interaction-Grounded Learning (IGL) is an example of such feedback-based reinforcement learning tasks where the learner optimizes the return by inferring latent binary rewards from the interaction with the environment. In the IGL setting, a relevant assumption used in the RL literature is that the feedback variable $Y$ is conditionally independent of the context-action $(X,A)$ given the latent reward $R$. In this work, we propose *Variational Information-based IGL (VI-IGL)* as an information-theoretic method to enforce the conditional independence assumption in the IGL-based RL problem. The VI-IGL framework learns a reward decoder using an information-based objective based on the conditional mutual information (MI) between the context-action $(X,A)$ and the feedback variable $Y$ observed from the environment. To estimate and optimize the information-based terms for the continuous random variables in the RL problem, VI-IGL leverages the variational representation of mutual information and results in a min-max optimization problem. Theoretical analysis shows that the optimization problem can be sample-efficiently solved. Furthermore, we extend the VI-IGL framework to general $f$-Information measures in the information theory literature, leading to the generalized $f$-VI-IGL framework to address the RL problem under the IGL condition. Finally, the empirical results on several reinforcement learning settings indicate an improved performance in comparison to the previous IGL-based RL algorithm.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义

**研究动机与背景**  
在强化学习（RL）的许多实际应用中（如脑机接口、推荐系统），智能体无法直接观测到奖励信号，只能从交互环境的反馈变量中推断潜在的二进制奖励。Interaction-Grounded Learning（IGL）正是此类问题的典型框架：智能体观察到上下文（context）并采取动作后，环境生成一个**未观测的二进制奖励**，同时返回一个多维反馈向量。为了使奖励推断可行，现有IGL文献假设反馈变量 $Y$ 在给定潜在奖励 $R$ 的条件下与上下文-动作 $(X,A)$ 条件独立（Full Conditional Independence）。然而，现实中反馈常受噪声干扰，该假设易被违反，导致现有算法性能下降。

**核心问题**：如何在IGL中**强制执行**条件独立性假设，从而更准确地推断隐式奖励，以提升在噪声反馈环境下的强化学习性能？

## 2. 论文提出的方法论

**核心思想**  
利用信息论中的条件互信息（Conditional Mutual Information, CMI）来度量变量间的依赖关系。条件独立性 $Y \perp\!\!\!\perp X,A \mid R$ 等价于 $I(Y; X,A \mid R)=0$。因此，学习奖励解码器 $\psi$ 使其解码出的奖励 $R_\psi$ 满足条件互信息最小化。

**关键技术细节**  
- **信息论目标函数**：  
  $$\arg\min_{\psi\in\Psi} \big\{ I(Y; X,A \mid R_\psi) - \beta \cdot I(X,A; R_\psi) \big\}$$  
  第一项强制条件独立性；第二项作为正则化项，防止解码器“过拟合”到噪声反馈，同时在无噪声场景下不会过度偏离最优解（定理3保证）。
- **变分表示与Min-Max优化**：  
  为处理连续随机变量（上下文 $X$ 和反馈 $Y$），利用Donsker-Varadhan变分表示，将互信息估计转化为一个min-max优化问题（定理1）：
  $$\min_{\psi}\max_{G}\min_{T} \Big\{ \mathbb{E}[G] - \mathbb{E}[e^G] - \beta\big(\mathbb{E}[T] - \mathbb{E}[e^T]\big) \Big\}$$
  其中 $G$ 和 $T$ 为神经网络参数化的判别器。通过梯度下降-上升（Gradient Descent Ascent）交替优化。
- **扩展到 $f$-信息**：  
  将KL互信息推广到一般 $f$-散度（如Pearson-$\chi^2$），提出 $f$-VI-IGL框架（定理4），提供算法2（$f$-VI-IGL）。
- **样本复杂度**：  
  定理2给出了优化问题样本复杂度上界（依赖反馈空间的覆盖数、奖励解码器输出范围等）。但针对深度神经网络，文中承认该界可能过大，属于深度学习泛化理论中的公开问题。

**算法流程（VI-IGL / $f$-VI-IGL）**  
1. 使用行为策略收集离线数据集 $\mathcal{D}_{\text{train}}$。  
2. 每轮：采小批量数据，通过增广方法（对每个样本 $N$ 次采样解码奖励）估计经验目标值。  
3. 交替更新判别器 $G$, $T$ 和奖励解码器 $\psi$ 的参数。  
4. 训练完成后，需在 $\psi$ 与 $1-\psi$ 中选择与真实奖励方向一致的那个（通过行为策略的低回报假设确定）。  
5. 用最终解码器训练离线上下文赌博机策略。

## 3. 实验设计

**数据集/场景**  
- **数字猜测任务**：从MNIST数据集随机抽取图片作为上下文，动作是预测数字（0-9），潜在奖励是预测是否正确。反馈图像：无噪声时为数字0或1的手写图片；带噪声时分别构造四种噪声类型：
  - **独立噪声（I）**：随机替换为字母‘t’或‘f’（来自EMNIST字母集）。
  - **动作包含噪声（A）**：替换为与动作相关的数字。
  - **上下文包含噪声（C）**：替换为与上下文标签相关的数字。
  - **上下文-动作包含噪声（C-A）**：替换为与两者相关的数字。
- **噪声水平**：10%、20%、30%。

**基准方法**  
- **E2G**（Xie et al., 2021b）：原始IGL算法。

**对比方法**  
- **VI-IGL**（本文标准KL互信息版本，$\beta=10$）  
- **VI-IGL ($\beta=0$)**：无正则化项  
- **不同 $f$-散度组合**：KL-KL, $\chi^2$-$\chi^2$, $\chi^2$-KL  
- **不同解码器输入**：仅反馈 $Y$ vs. 上下文-动作-反馈 $(X,A,Y)$

## 4. 资源与算力

**未明确说明**。论文未提及GPU型号、数量、训练时长等具体算力信息。仅在实验细节中说明训练了1000个epoch，batch size 600，每500轮交替更新参数，并使用了梯度裁剪和指数移动平均。可以推断实验规模中等，但无具体资源数据。

## 5. 实验数量与充分性

**实验数量**  
- 主要对比：4种噪声类型 × 3个噪声水平（0%, 10%, 20%, 30%）× 16次随机试验 → 大量重复实验。  
- 消融实验：
  - 正则化强度 $\beta$（表9、10，图3）：5个值（0,5,10,15,20）。  
  - $f$-散度选择（表3）：3种组合。  
  - 解码器输入类型（表4）：2种。  
- 总实验量较为充分，每次结果报告均值±标准差，统计严谨。

**充分性与客观性**  
- 实验覆盖了多种噪声场景，与真实应用中可能的噪声类型（独立、依赖动作、依赖上下文）相符。  
- 与强基线E2G对比，且在无噪声环境下VI-IGL性能与E2G接近（81.6% vs 82.2%），表明方法在理想条件下不退化。  
- 消融实验系统性地验证了正则化项、$f$-散度、解码器输入的必要性。  
- 但：
  - 仅使用了单一任务（数字猜测），缺乏更复杂环境（如推荐系统、机器人控制）的验证。  
  - 未与最新Action-Inclusive IGL (Xie et al., 2022) 对比（论文提及但未实验）。  
  - 超参数 $\beta$ 的选择需手动调优，实验中对不同噪声使用了相同 $\beta=10$，实际可能需针对场景调整。

## 6. 论文的主要结论与发现

1. **VI-IGL显著优于E2G**：在所有噪声类型和噪声水平下，VI-IGL的精度均大幅高于E2G（例如在10%独立噪声下：71.0% vs 25.0%）。  
2. **正则化项至关重要**：添加 $\beta I(X,A; R_\psi)$ 项显著提升了鲁棒性（$\beta=10$ 比 $\beta=0$ 在噪声环境下精度提高10-20个百分点，标准差也更小）。  
3. **反馈依赖解码器更好**：仅以 $Y$ 为输入的解码器优于以 $(X,A,Y)$ 为输入的解码器。  
4. **不同 $f$-散度各有优劣**：KL-KL 和 $\chi^2$-$\chi^2$ 在不同噪声类型下表现不同，无统一最优选择。  
5. **正则化几乎不破坏条件独立性**：在可实现假设下，最优解码器仍满足条件独立性（定理3）。

## 7. 优点

- **理论扎实**：从信息论角度重新形式化IGL问题，给出条件互信息与条件独立的等价关系，并推导变分优化形式。  
- **鲁棒性设计**：引入正则化项针对噪声反馈，理论证明了正则化对条件独立性的“几乎保持”。  
- **通用框架**：扩展到 $f$-信息，提供了多种散度选择，可适应不同噪声结构。  
- **样本复杂度分析**：提供了有限样本下的泛化界（尽管对深度网络可能保守）。  
- **实验设计完整**：多种噪声类型、噪声水平、消融实验，统计量规范（均值±标准差，16次重复）。

## 8. 不足与局限

- **任务单一**：仅在一个数字猜测任务上验证，缺少更复杂的IGL应用（如推荐系统、BCI）。  
- **基线不够新**：仅与E2G对比，未与Action-Inclusive IGL (Xie et al., 2022) 等后续工作比较。  
- **超参数敏感**：$\beta$ 需要调优，实验中虽给出不同 $\beta$ 结果，但未提供自动选择方法。  
- **样本复杂度界不紧**：对深度神经网络的泛化界过于悲观，文中承认是公开问题。  
- **方差较大**：实验结果显示标准差较高（如10%噪声下16%），可能存在不稳定问题。  
- **训练细节**：交替训练策略（500轮更新判别器，500轮更新解码器）可能引入额外超参数，未充分讨论其敏感性。  
- **资源消耗未知**：未报告计算成本，难以评估方法在更大规模问题上的可行性。

（完）
