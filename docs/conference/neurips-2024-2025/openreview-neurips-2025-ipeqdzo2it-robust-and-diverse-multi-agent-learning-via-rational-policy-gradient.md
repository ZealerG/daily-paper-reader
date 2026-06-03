---
title: Robust and Diverse Multi-Agent Learning via Rational Policy Gradient
title_zh: 通过理性策略梯度实现鲁棒且多样的多智能体学习
authors: "Niklas Lauffer, Ameesh Shah, Micah Carroll, Sanjit A. Seshia, Stuart Russell, Michael D Dennis"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ipEqdzO2IT"
tags: ["query:graph-part"]
score: 8.0
evidence: 多智能体强化学习与并行决策
tldr: 本文针对多智能体对抗优化中合作场景下的自我破坏问题，提出了理性保持策略优化（RPO）。该方法通过确保智能体的策略相对于某些可能的伙伴策略是最优的，来避免非理性的自我破坏。实验表明，RPO能够在合作任务中学习到鲁棒且多样的策略，推动了多智能体强化学习的并行决策能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1424, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 479, \"height\": 200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 726, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 298, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1419, \"height\": 1753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 447, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 597, \"height\": 207, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1386, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 305, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1437, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 987, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 856, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 658, \"height\": 172, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 989, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 987, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 986, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ipeqdzo2it/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 988, \"height\": 371, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 950, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1380, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 659, \"height\": 137, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 809, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ipeqdzo2it/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 667, \"height\": 226, \"label\": \"Table\"}]"
motivation: 现有对抗优化在多智能体合作中导致智能体自我破坏，阻止任务完成。
method: 提出理性保持策略优化，确保智能体策略相对于可能的伙伴策略保持理性。
result: 在合作多智能体任务中学习到鲁棒且多样的策略，避免自我破坏。
conclusion: 理性保持策略优化是合作多智能体学习中对抗优化的有效范式。
---

## Abstract
Adversarial optimization algorithms that explicitly search for flaws in agents' policies have been successfully applied to finding robust and diverse policies in the context of multi-agent learning. However, the success of adversarial optimization has been largely limited to zero-sum settings because its naive application in cooperative settings leads to a critical failure mode: agents are irrationally incentivized to *self-sabotage*, blocking the completion of tasks and halting further learning. To address this, we introduce *Rationality-preserving Policy Optimization (RPO)*, a formalism for adversarial optimization that avoids self-sabotage by ensuring agents remain *rational*—that is, their policies are optimal with respect to some possible partner policy. To solve RPO, we develop *Rational Policy Gradient (RPG)*, which trains agents to maximize their own reward in a modified version of the original game in which we use *opponent shaping* techniques to optimize the adversarial objective. RPG enables us to extend a variety of existing adversarial optimization algorithms that, no longer subject to the limitations of self-sabotage, can find adversarial examples, improve robustness and adaptability, and learn diverse policies. We empirically validate that our approach achieves strong performance in several popular cooperative and general-sum environments. Our project page can be found at https://rational-policy-gradient.github.io.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：多智能体强化学习（MARL）中，对抗优化（adversarial optimization）在零和博弈中成功用于寻找策略漏洞、提升鲁棒性和多样性。然而，在**合作或一般和（general-sum）**场景中，直接应用对抗优化会导致**自我破坏（self-sabotage）**问题：智能体为最小化队友的奖励，会主动破坏任务完成，反而阻碍学习。
- **核心问题**：如何在合作/一般和设定下进行对抗优化，同时避免自我破坏，从而学习鲁棒且多样的策略。
- **整体含义**：本文提出**理性保持策略优化（RPO）**框架，通过约束对抗智能体的策略必须对某些可能的队友策略是最优的（即保持理性），消除自我破坏。并进一步设计**理性策略梯度（RPG）**算法求解RPO，将对抗优化的成功扩展到合作领域。

## 2. 论文提出的方法论

### 核心思想
- **RPO形式化**：对于每个智能体\(i\)，给定对抗性优化目标\(O_i\)，RPO要求智能体\(i\)的策略必须是对某个可能协策略\(\pi'_{-i}\)的最优反应（即\(\pi_i \in \text{BR}(\pi'_{-i})\)）。这保证了智能体不会采取非理性行为（如故意牺牲自身奖励）。
- **RPG算法**：通过引入**操纵器（manipulator）智能体**来间接实现RPO。每个基础智能体( base agent )不再直接优化\(O_i\)，而是最大化自身在修改后游戏中的奖励（与操纵器合作），以保证理性。操纵器则负责优化原始对抗目标\(O_i\)，但只能通过影响基础智能体的学习过程（使用**对手塑造（opponent shaping）**技术）来实现。

### 关键技术细节
- **梯度更新**：使用**Loaded DiCE**（一种高阶无偏梯度估计器）计算操纵器的梯度，允许通过自动微分获取对基础智能体更新后的目标\(O_i\)的梯度。
- **前瞻步（lookahead）**：操纵器在更新时考虑基础智能体经过若干步梯度下降后的结果（前瞻更远的未来），帮助稳定学习和收敛。
- **伙伴游戏正则化（partner-play regularization）**：为基础智能体引入少量与评估时队友（其他基础智能体）共同采样的轨迹，减轻分布偏移，防止操纵器通过把基础智能体推离分布来取巧。

### 算法流程（文字描述）
1. 复制当前基础策略参数\(\theta_i' \leftarrow \theta_i\)。
2. 对\(N\)步前瞻：在\(\theta_i'\)和操纵器策略\(\theta^M_{-i}\)下采样，用RL损失（含伙伴游戏正则化）更新\(\theta_i'\)。
3. 在更新后的基础策略之间采样（用于评估原始目标\(O_i\)）。
4. 用Loaded DiCE损失计算操纵器梯度，更新\(\theta^M_{-i}\)，使其通过基础智能体的学习过程影响\(O_i\)。
5. 一步更新基础智能体\(\theta_i\)（与前瞻步相同，但不考虑操纵器）。

- **RPG的多种变体**：基于RPG扩展了五种现有算法：
  - **AP-RPG**（对抗策略）：寻找预训练策略的理性漏洞。
  - **AT-RPG**（对抗训练）：同时训练受害者与对抗者，提升鲁棒性。
  - **PAIRED-RPG**（基于遗憾的对抗训练）：训练主角和对手，通过最大遗憾产生课程。
  - **PAIRED-A-RPG**（固定主角的攻击变体）：寻找最大遗憾的对抗策略。
  - **XPD-RPG**（交叉游戏多样性）：训练多样化且理性的策略群体，避免自我破坏。

## 3. 实验设计

### 使用的环境（场景）
1. **矩阵博弈**：零和、合作、混合动机等不同支付矩阵。
2. **Overcooked**：多人合作烹饪游戏，使用五种布局（Cramped Room, Forced Coordination, Counter Circuit, Coordination Ring, Asymmetric Advantages）。
3. **STORM**：空间-时间矩阵游戏，原始版及两种修改版（无观察队友位置、引入可自我破坏的惩罚区域）。
4. **Hanabi**：简化版（3色/3等级 和 4色/4等级）的合作不完全信息卡牌游戏。

### 基准（Benchmark）与对比方法
- **自我对抗（Self-Play, SP）**：不同熵系数版本。
- **对抗策略（AP）** 与 **对抗训练（AT）**（原始非RPG版）。
- **PAIRED**（原始非RPG版）。
- **交叉游戏多样性基线（XPD）**：类似于LIPO和ADVERSITY。
- **CoMeDi**（当前防止自我破坏的SOTA算法，基于观察分布混淆）。

### 评价指标
- 自我对抗奖励、交叉游戏奖励、跨种群交叉游戏平均奖励、对抗攻击下受害者剩余奖励。
- 对于多样性任务，还比较策略间的交叉游戏分数以衡量真实不兼容性。

## 4. 资源与算力

- 所有实验运行在**单GPU**（混合使用NVIDIA A4000和A6000）上，使用**本地SLURM集群**，配备**32个CPU核心和50GB RAM**。
- 每个种子（seed）的训练时间从**1分钟到24小时不等**（取决于环境和算法复杂度）。
- 未详细报告总GPU小时数，但可推断总计算量适中（矩阵博弈很快，Overcooked和Hanabi需要数小时）。

## 5. 实验数量与充分性

- **实验数量**：覆盖4类环境（矩阵、Overcooked多个布局、STORM多个变种、Hanabi两个版本），对每种环境进行了多种算法对比，并报告了多次重复（种子数见正文，如Overcooked使用5个种子）。还展示了消融（如前瞻步数的影响）和多种对抗攻击测试。
- **充分性与公平性**：
  - 实验设计较好地覆盖了合作、混合动机、零和场景，验证了RPO/RPG在不同设定下的有效性。
  - 对比方法包括经典自我对抗、现有对抗优化算法（无RPO）以及专为防止自我破坏设计的CoMeDi，对比全面。
  - 报告了置信区间、标准误差，并提供了可视化结果（如交叉游戏热力图、训练曲线）。
  - 但未进行大规模超参数网格搜索，超参数通过少量调试确定，可能存在过拟合风险。
  - 环境规模相对较小（简化版Hanabi，小地图Overcooked），未见大规模复杂环境（如完整Hanabi 5色或更大Overcooked布局）的验证。

## 6. 论文的主要结论与发现

- **Claim 1：RPG可学习有意义多样的策略**：在STORM和Overcooked中，XPD-RPG生成在自对抗中高分、交叉对抗中低分但非自毁的策略（例如在STORM中收集不同颜色硬币，但仍能部分适应），而CoMeDi和传统XPD往往选择自我破坏（如站在原地阻碍送餐）。
- **Claim 2：RPG训练出更鲁棒的策略**：在Overcooked和Hanabi中，XPD-RPG训练的种群内交叉游戏平均奖励显著高于SP和XPD；XPD-RPG策略与任何伙伴（包括其他算法训练的伙伴）配合时得分更高，说明其泛化能力更强。
- **Claim 3：RPG能发现理性的对抗样本**：在STORM中，AP-RPG和PAIRED-A-RPG找到了受害者策略的理性漏洞（如利用受害者不会逆时针绕行的习惯），而不像非RPG版本直接自我破坏导致零奖励。
- **Claim 4：RPG有效防止自我破坏**：在矩阵博弈、STORM、Overcooked中，RPG变体均未出现自毁行为，而所有非RPG对抗算法（AT、PAIRED、XPD）均因自毁而训练失败或生成无效策略。
- **额外发现**：适当的前瞻步数（lookahead steps）有助于稳定收敛到平衡策略（如矩阵博弈中均匀混合策略）。

## 7. 优点

- **方法创新**：提出RPO形式化解解决合作场景中对抗优化的自毁问题，理论上严谨。
- **通用性**：RPG可作为插件，扩展多种对抗优化算法（AP、AT、PAIRED、XPD），覆盖了鲁棒性、多样性、攻击等多种应用。
- **实验设计亮点**：
  - 使用矩阵博弈进行概念验证，直观展示理性约束的效果。
  - 通过多种环境验证，包括合作（Overcooked、Hanabi）和一般和（STORM）设定。
  - 对比了当前SOTA方法CoMeDi，并指出其失败原因（无法在单一观察状态下防止自毁）。
  - 提供了详细的超参数和计算资源信息，便于复现。
  - 附有项目页面和代码，增强可重复性。
- **可视化与定性分析**：通过交互式可视化、训练曲线、热力图等展示了策略行为，帮助理解。

## 8. 不足与局限

- **计算开销**：RPG需要计算高阶梯度（通过对手塑造），训练速度比普通对抗算法慢约3倍（XPD-RPG比XPD慢3倍），在更大规模环境中可能难以扩展。
- **高方差**：高阶梯度从样本中估计，方差大，需要较大批量才能稳定训练，可能限制实际应用。
- **缺乏形式化收敛保证**：RPG虽然直觉上保证理性，但论文未给出严格的理论收敛证明，仅通过实验验证。
- **环境规模有限**：实验使用简化版Hanabi（3/4色）和较小Overcooked布局，未测试完整Hanabi 5色或更复杂合作任务（如Starcraft II等），泛化性存疑。
- **超参数敏感**：多项超参数（学习率、伙伴游戏系数、前瞻步数、操纵器学习率等）需要针对不同环境调整，未提供系统自动调参方案。
- **鲁棒性验证不够全面**：仅测试了固定策略下的对抗攻击，未考虑人类合作伙伴或动态变化的对手；也未深入分析训练奖励与真实合作性能之间的差距。
- **与CoMeDi的比较**：论文指出CoMeDi在矩阵博弈中失败，但CoMeDi的设计初衷是针对部分可观测历史的混淆，可能不完全适用于全观测环境，对比条件可能对CoMeDi不利。

（完）
