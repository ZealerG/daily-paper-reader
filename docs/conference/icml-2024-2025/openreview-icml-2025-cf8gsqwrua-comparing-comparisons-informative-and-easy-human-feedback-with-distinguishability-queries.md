---
title: "Comparing Comparisons: Informative and Easy Human Feedback with Distinguishability Queries"
title_zh: 比较比较：通过可区分性查询实现信息丰富且易用的人类反馈
authors: "Xuening Feng, Zhaohui JIANG, Timo Kaufmann, Eyke Hüllermeier, Paul Weng, Yifei Zhu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Cf8gsqWrua"
tags: ["query:graph-part"]
score: 8.0
evidence: 利用可区分性查询的人类反馈强化学习方法
tldr: 针对偏好反馈中难以比较细微差异和只能传递排序信息的问题，本文提出可区分性查询，让标注者比较两对轨迹的区分难度后再提供反馈。实验表明该方法在获得更丰富偏好信息的同时减轻了标注负担，提升了RLHF的效率和效果。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 846, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1716, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1712, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 380, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 819, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 814, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cf8gsqwrua/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1439, \"height\": 626, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cf8gsqwrua/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 894, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cf8gsqwrua/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1783, \"height\": 831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cf8gsqwrua/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1327, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cf8gsqwrua/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1871, \"height\": 451, \"label\": \"Table\"}]"
motivation: 传统偏好反馈难以比较细微差异且信息量有限。
method: 提出可区分性查询，让标注者先选较易区分的一对再反馈。
result: 在多个任务上提升了反馈信息量和学习效率。
conclusion: 可区分性查询为RLHF提供了一种更高效的反馈机制。
---

## Abstract
Learning human objectives from preference feedback has significantly advanced reinforcement learning (RL) in domains where objectives are hard to formalize. 
However, traditional methods based on pairwise trajectory comparisons face notable challenges, including the difficulty in comparing trajectories with subtle differences and the limitation of conveying only ordinal information, limiting direct inference of preference strength. 
In this paper, we introduce a novel *distinguishability query*, enabling humans to express preference strength by comparing two pairs of trajectories. 
Labelers first indicate which of two pairs is easier to distinguish, then provide preference feedback only on the easier pair. 
Our proposed query type directly captures preference strength and is expected to reduce the cognitive load on the labeler. 
We further connect this query to cardinal utility and difference relations and develop an efficient query selection scheme to achieve a better trade-off between query informativeness and easiness. 
Experimental results demonstrate the potential of our method for faster, data-efficient learning and improved user-friendliness in RLHF benchmarks, particularly in classical control settings where preference strength is critical for expected utility maximization.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统基于成对轨迹比较的偏好反馈存在两大局限：一是人类难以比较细微差异的轨迹，导致查询效率低、用户体验差；二是成对比较仅传递序数信息（谁更好），无法直接表达偏好强度（好多少），而强化学习期望效用最大化本质上需要基数效用。
- **研究背景**：偏好反馈已成功应用于RLHF（如语言模型微调、机器人训练），但上述局限限制了其效果。现有工作在减少标注负担方面有预训练、允许放弃回答、查询选择等策略，但缺乏同时解决信息量和易答性的统一方法。
- **整体含义**：提出一种新的查询类型——可区分性查询（Distinguishability Query），让人类优先比较更容易区分的轨迹对，从而同时获得偏好强度信息和减轻认知负担。

## 2. 论文提出的方法论

### 核心思想
- **可区分性查询（DQ）**：向人类展示两个成对比较查询（PCQ），要求先选出哪个PCQ更容易区分（即偏好强度差异更大），然后仅对该选中的PCQ提供偏好反馈。反馈由两部分组成：可区分性偏好d（指示哪个PCQ更易区分）和选中的PCQ的偏好标签y_PCQ。
- **理论连接**：将DQ与基数效用和差异关系（difference relation）建立联系，可区分性度量定义为轨迹回报之差（公式3），利用Bradley-Terry模型建模选择更易区分PCQ的概率（公式7）。

### 关键技术细节
1. **查询选择方案**（图2）：
   - 从轨迹缓冲区中随机采样段对得到候选PCQ集Qp。
   - **信息性筛选**：基于集成奖励模型预测的方差（公式5）选取top nI个信息性高的PCQ（高方差意味着高认知不确定性）。
   - **易答性筛选**：在信息性高的PCQ中，基于预测熵的负值（公式6）选取top nE和bottom nE个易答的PCQ（低熵对应易区分）。
   - **配对**：将易答性排序后，第i个最易答的与第(i+nE)个最易答的配对构成一个DQ。
2. **训练目标**（公式9）：
   - 组合两个损失：可区分性偏好损失（公式8，交叉熵）和选中的PCQ的偏好损失（公式2，交叉熵），权重为λd和λp。
   - 利用DQ反馈同时优化奖励模型：区分强度信号（d）和强偏好信号（y_PCQ）。
3. **算法流程**（Algorithm 1）：在PEBBLE框架上修改，每次反馈会话中生成DQ，收集反馈后更新奖励模型，同时使用SAC优化策略。

## 3. 实验设计

### 任务/数据集
- **DeepMind Control Suite (DMControl)**：Walker walk、Quadruped walk、Humanoid stand（回报指标）。
- **Meta-World**：Window open、Door unlock、Door open、Sweep into、Disassemble（成功率指标）。
- 共3个运动任务 + 5个操作任务，采用无真实奖励设置，仅接收合成或人类反馈。

### Benchmark
- **基线方法**：PEBBLE（熵选择）、SURF（方差+半监督）、RUNE（方差+内在奖励）、MRN（双层优化）、QPA（近策略随机选择），均使用成对比较查询。
- **上限**：使用真实奖励的SAC。

### 查询预算
- 各任务预算不同（如Walker walk 200次、Quadruped walk 500次等），DistQ分别报告全预算和半预算（DQ (half)）以公平比较——因为一个DQ只要求标注者对选中的一对反馈，相当于只消耗一次比较精力。

## 4. 资源与算力

- **文中说明**：所有实验仅需1张GPU卡；使用多种平台（GeForce RTX 3060 12G、RTX 2070 SUPER、RTX 2060等），内存32-64GB，CPU Intel i7系列。
- **训练时长**：相同平台下各方法训练时间相似（最长不超过12小时），DistQ未带来额外计算成本。
- **未说明**：具体运行次数总耗时、GPU小时数未给出。

## 5. 实验数量与充分性

- **组数**：
  - 主实验：8个任务（3个运动+5个操作），每种方法5次运行，报告均值和标准差。
  - 消融实验（Section 5.5）：三个维度：
    1. 查询选择策略：对比Full方法（先信息性后易答）、反序（先易答后信息性）、仅信息性、仅易答。
    2. PCQ配对方式：对比提出的排序配对 vs. 随机配对。
    3. 损失函数：对比全损失、仅使用成对偏好损失（去掉区分性损失）、PEBBLE。
  - 用户研究：1个任务（Quadruped waving），真实人类标注者，150次查询，对比DistQ与PEBBLE。
  - 额外给出易答性指标（错误预测次数）实验（图4）。
- **充分性**：实验覆盖了多种控制任务（连续动作、高维、稀疏奖励）、多种路径（最终性能、学习曲线、用户反馈），消融实验验证了每个组件贡献。对比基线均为SOTA，且采用相同基础框架（PEBBLE）保证公平。但任务均限于经典控制/机器人操作，未涉及语言模型或真实机器人。

## 6. 论文的主要结论与发现

- **性能提升**：DistQ（全预算）在7/8个任务上优于所有基线，在Humanoid stand上略低于QPA但仍具竞争力。半预算也常优于多数基线。
- **易答性改善**：DistQ在训练过程中错误预测反馈的次数最少（图4），表明选出的PCQ更容易被人类准确回答。
- **消融证实**：
  - 先信息性后易答策略优于反序、仅信息性或仅易答（图5）。
  - 提出的配对方式显著优于随机配对（图6）。
  - 区分性损失贡献重要：去掉后性能下降，但仅用成对损失依然优于PEBBLE，说明查询选择本身也有改进。
- **用户研究**：真实人类标注者反馈DistQ更易回答，最终策略成功率100% vs. PEBBLE 0%。

## 7. 优点

- **创新查询类型**：首次引入可区分性查询，同时获取偏好强度信息和减轻标注负担，与决策理论中差异关系紧密连接。
- **高效查询选择**：结合信息性（方差）和易答性（负熵）两步筛选，实现平衡，兼顾学习效率和用户体验。
- **统一训练目标**：将区分性和偏好反馈整合至损失函数，直接利用强度信号提升奖励模型质量。
- **灵活性**：可应用于任何基于成对比较的RLHF方法（文章基于PEBBLE实现）。
- **实验全面**：覆盖多种任务、多个基线、多项消融，并有真实用户验证，结论稳健。

## 8. 不足与局限

- **任务范围有限**：仅评估了经典控制/操作任务，未涉及语言模型、LLM微调等实际RLHF场景；未来工作需扩展到更多领域。
- **信息性/易答性度量简单**：当前使用方差和熵，可能存在更优或更复杂的度量（如考虑人类认知模型），或许能进一步优化。
- **公平比较困难**：DistQ的查询结构不同，作者用全预算和半预算来框定范围，但并未严格等价于相同人工成本比较（标注者需先比较两对再对一对反馈）。
- **用户研究规模很小**：仅1名参与者、1个任务、约3小时；缺乏统计显著性和多样性。
- **依赖合成反馈假设**：主要实验使用合成Oracle（基于真实奖励的Bradley-Terry模型），未验证在真实人类反馈中噪声更大、一致性更低时的表现。
- **未讨论算法复杂度**：查询选择需要计算所有候选PCQ的方差和熵，可能在大规模数据中带来额外开销。

（完）
