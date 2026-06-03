---
title: "ARS: Adaptive Reward Scaling for Multi-Task Reinforcement Learning"
title_zh: ARS：多任务强化学习的自适应奖励缩放
authors: "Myungsik Cho, Jongeui Park, Jeonghye Kim, Youngchul Sung"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=U0mI6M7lvI"
tags: ["query:graph-part"]
score: 7.0
evidence: 多任务强化学习中的自适应奖励缩放
tldr: 本文针对多任务强化学习中任务复杂度和奖励分布差异大的问题，提出自适应奖励缩放（ARS）框架。通过基于历史的奖励缩放策略和周期性网络重置机制，平衡不同任务的奖励分布，提升训练稳定性和效率。在Meta-World基准上显著超越基线方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 814, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 816, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 766, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1707, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1700, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1030, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 863, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 857, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1294, \"height\": 952, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u0mi6m7lvi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1250, \"height\": 1517, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 893, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 895, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 894, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 893, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1513, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 579, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 918, \"height\": 872, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1160, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1251, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u0mi6m7lvi/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1773, \"height\": 294, \"label\": \"Table\"}]"
motivation: 多任务强化学习面临任务奖励分布不均的挑战。
method: 自适应奖励缩放与周期重置机制。
result: 在Meta-World上表现优异。
conclusion: 为多任务强化学习提供了有效的奖励调节方法。
---

## Abstract
Multi-task reinforcement learning (RL) encounters significant challenges due to varying task complexities and their reward distributions from the environment. To address these issues, in this paper, we propose Adaptive Reward Scaling (ARS), a novel framework that dynamically adjusts reward magnitudes and leverages a periodic network reset mechanism. ARS introduces a history-based reward scaling strategy that ensures balanced reward distributions across tasks, enabling stable and efficient training. The reset mechanism complements this approach by mitigating overfitting and ensuring robust convergence. Empirical evaluations on the Meta-World benchmark demonstrate that ARS significantly outperforms baseline methods, achieving superior performance on challenging tasks while maintaining overall learning efficiency. These results validate ARS's effectiveness in tackling diverse multi-task RL problems, paving the way for scalable solutions in complex real-world applications.

---

## 论文详细总结（自动生成）

# 基于论文《ARS: Adaptive Reward Scaling for Multi-Task Reinforcement Learning》的详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：多任务强化学习（Multi-task RL）面临两大挑战：一是**负迁移**（学习一个任务干扰其他任务），二是**奖励尺度（reward scale）在不同任务间差异悬殊**，导致训练偏向高奖励任务，困难任务（如Meta-World中的push、pick-place、peg-insert-side）因初始奖励过低而完全无法学习。
- **现有方法局限**：虽然固定奖励缩放（如放大100倍）在单任务中有效，但在多任务场景下会因某些任务奖励被过度放大而引发过拟合，降低整体性能。
- **论文整体含义**：提出自适应奖励缩放（ARS）框架，通过动态调整各任务的奖励缩放因子，并结合周期性网络重置，实现多任务之间平衡、稳定的训练，显著提升困难任务的学习效果。

## 2. 论文提出的方法论

### 核心思想
- 利用每个任务的**经验回放缓冲池（replay buffer）** 中奖励的历史分布信息，动态计算缩放因子，使所有任务的**平均奖励**被统一到相同的量级，从而避免因原始奖励差异导致的训练偏置。
- 配合**周期性网络参数重置**（保留回放缓冲池），缓解因缩放因子变化引起的批评者网络训练不稳定以及早期任务偏置。

### 关键技术细节
1. **基于历史平均奖励的缩放策略（公式6）**：
   - 对每个任务 \( \mathcal{T}_i \)，从该任务专属的回放缓冲池 \( \mathcal{D}_i \) 中计算当前平均奖励 \( \bar{r}_i \)。
   - 缩放因子定义为：
     \[
     c_i^{\text{rew}} = \frac{\max\{\bar{r}_1, \ldots, \bar{r}_N\}}{\bar{r}_i}
     \]
   - 即所有任务中的最大平均奖励除以当前任务的平均奖励，使得缩放后各任务的奖励平均值一致。
2. **修改后的批评者损失（公式7）**：
   - 将原始奖励 \( r \) 替换为缩放后的奖励 \( c_i^{\text{rew}} r \)，再计算 TD 误差。
3. **重置机制**：
   - 仅在重置时刻更新缩放因子，其余时间保持固定，避免批评者目标频繁波动。
   - 重置时随机重新初始化策略网络和Q值网络参数，但保留所有回放缓冲池数据，使模型能够快速从高质量经验中恢复并克服初始偏置。

### 算法流程（Algorithm 1）
1. 初始化策略 \( \pi_\theta \)、Q函数 \( Q_\psi \)、每个任务各一个回放缓冲池 \( \mathcal{D}_i \)。
2. 用随机策略填充各缓冲池一定步数。
3. 用公式(6)初始化各任务缩放因子。
4. 循环训练：
   - 每个任务与环境交互并存储经验。
   - 使用缩放后的奖励更新 \( \theta, \psi \)。
   - 每达到重置周期 \( T_{\text{reset}} \)，更新缩放因子并重置网络参数。

### 增强版本
- **ARS-LN**：在批评者网络输入和隐藏层加入层归一化（Layer Normalization）。
- **ARS-LoRA**：在ARS-LN基础上，训练后期（MT10在75%、MT50在83.3%步长后）引入低秩适应（LoRA），添加少量任务专用参数，进一步提升性能。

## 3. 实验设计

### 数据集/场景与Benchmark
- **Meta-World benchmark**（Yu et al., 2019）：包含50个Sawyer机械臂操控任务，使用MuJoCo物理引擎。
- **两个标准子集**：
  - **MT10**：10个任务（reach, push, pick-place, door-open, drawer-open, drawer-close, button-press-topdown, peg-insert-side, window-open, window-close）。
  - **MT50**：全部50个任务。
- **评价指标**：成功比率（success ratio），每个任务评估10个随机目标的平均成功率。MT50额外报告“底部k个任务的平均成功率”（Bottom-k），聚焦困难任务。

### 对比方法
- **SAC-MT**：基础多任务SAC，使用one-hot任务编码。
- **SAC-MT-MH**：每个任务独立的策略输出头（multi-head）。
- **Soft Modular**：软模块化策略网络。
- **PCGrad**：梯度手术（冲突梯度投影）。
- **PaCo**：参数组合性多任务RL。
- **MOORE**：混合正交专家。
- **SMT**：任务调度（“Hard Tasks First”）+重置。
- 另外还测试了将ARS集成到PCGrad、Soft Modular、MOORE中的效果。

## 4. 资源与算力

论文**未明确说明具体使用的GPU型号、数量或训练时长**，仅提供了训练步数：MT10为2×10⁷步，MT50为1×10⁸步。未提及所需的具体计算资源或运行时间。因此无法量化算力消耗。

## 5. 实验数量与充分性

- **主要实验结果**（表1、表2）：MT10和MT50各报告了8个随机种子的均值和标准差，覆盖所有对比方法。
- **消融实验**（表4、5、6、9、10、11）：
  - 组件消融（去掉重置或去缩放）。
  - 缩放方式对比（均值、标准差、归一化）。
  - 网络容量影响（不同隐藏层大小）。
  - 重置次数 \( n_{\text{reset}} \) 的影响。
  - 重置网络类型（仅重置批评者 vs 重置所有）。
  - 与PopArt对比。
  - 不同horizon长度（500 vs 150）。
- **集成实验**（表3）：将ARS集成到4种其他方法后对比。
- **额外分析**：绘制缩放因子变化曲线（图5）、Q值曲线（图3、6）、ESTR曲线（图4）、学习曲线（附录D）。
- **充分性评价**：实验设计较为全面，覆盖了主要组件、超参数、网络架构、与先进方法的对比等维度；采用多次随机种子确保可靠性；对比方法均为近年代表性工作。但**全部实验仅在Meta-World一个benchmark上进行**，未验证在其他领域（如Atari、机器人其他场景）的泛化性，存在领域单一的风险。

## 6. 论文的主要结论与发现

- ARS在MT10上达到 **97.3%～99.5%** 的平均成功率（ARS-LoRA），首次以从头训练的多任务范式**完全解决MT10所有任务**。
- 在MT50上，ARS-LN/ARS-LoRA平均成功率分别达到 **78.3%和83.2%**，底部10个最困难任务的成功率从0%提升至9.1%～29.3%，显著超越所有基线。
- **缩放因子动态变化**（图5）显示：困难任务初始被赋予高缩放因子，随着学习进行逐渐下降，表明任务获得充分训练后奖励增加，自动降低放大倍数。
- **ARS可即插即用**，集成到SAC-MT、PCGrad、Soft Modular、MOORE中均能带来一致、大幅的性能提升（MT50提升至少20个百分点）。
- 重置机制与自适应缩放在消除偏置和稳定训练中缺一不可；使用均值进行缩放优于标准差或归一化方法。
- 增大网络容量（从400到1024）时，ARS性能持续提升，而普通SAC-MT则无增益，表明ARS能更有效利用大模型。

## 7. 优点

- **方法简洁高效**：仅需计算每个任务回放缓冲池的奖励均值作为缩放依据，无需额外超参数或复杂优化；重置机制复用已成熟的单任务重置技术。
- **针对性强**：直接解决多任务RL中容易被忽视的奖励尺度异质性问题，而非仅关注梯度冲突或网络架构。
- **通用性与兼容性**：可作为插件集成到任何离策略多任务RL算法中，实验证实其普适性。
- **实验结果突出**：在公认困难的Meta-World MT50上首次达到80%以上平均成功率，且底部任务表现远优于现有方法。
- **充分的消融与分析**：通过多组实验揭示了组件贡献、缩放策略选择、容量扩展规律等，理论支撑扎实。

## 8. 不足与局限

- **基准单一**：仅使用Meta-World，缺乏在Atari、DeepMind Control Suite等其他多任务RL基准上的验证，泛化能力存疑。
- **超参数敏感**：重置次数 \( n_{\text{reset}} \) 需要预先设定（MT10用4，MT50用6），论文虽做了简单消融（图11）但未深入探讨自适应确定方法，且LoRA的激活时机和秩也需人工设定。
- **非平稳性问题**：动态缩放因子导致批评者目标在重置前固定、重置时突变，可能对学习稳定性仍有潜在影响，论文未详细分析收敛性。
- **计算开销**：虽然缩放计算本身轻量，但重置机制需要重新初始化网络并重放经验，训练初期的探索阶段可能延长；实际训练时间未报告，无法评估效率。
- **与其他高级方法结合有限**：仅测试了集成到少数方法，未涉及基于蒸馏、任务编码等更复杂框架，兼容性边界不清晰。
- **奖励缩放假设**：方法假设回放缓冲池中的平均奖励能正确反映任务难度，但若某些任务虽然初始奖励低但容易学习（如随机探索即可获得高奖励），该假设可能不成立。论文未讨论这类边际情况。

（完）
