---
title: Reinforcement learning for one-shot DAG scheduling with comparability identification and dense reward
title_zh: 基于强化学习的单次DAG调度：比较性识别与密集奖励
authors: "Xumai Qi, Dongdong Zhang, Taotao Liu, Hongcheng Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KDKddNgeKo"
tags: ["query:graph-part"]
score: 4.0
evidence: 基于策略梯度和密集奖励的强化学习DAG调度方法
tldr: 现有基于强化学习的DAG调度方法存在采样概率估计偏差和稀疏奖励问题。本文提出基于策略梯度的单次DAG调度方法，引入可比较反链识别机制和密集奖励信号，消除了冗余比较并提高了训练效率。实验证明该方法在调度性能上优于现有技术。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kdkddngeko/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1269, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kdkddngeko/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1002, \"height\": 179, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kdkddngeko/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1420, \"height\": 770, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kdkddngeko/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 508, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1427, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1089, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1391, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 915, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1419, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kdkddngeko/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1478, \"height\": 375, \"label\": \"Table\"}]"
motivation: 现有基于RL的DAG调度方法因冗余节点优先级比较和稀疏奖励导致训练效率低下。
method: 提出可比较反链识别机制消除冗余比较，设计密集奖励信号提供及时反馈，基于策略梯度框架。
result: 在多个DAG调度基准上，该方法相比现有方法取得了更好的调度质量和更快的收敛速度。
conclusion: 结合比较性识别和密集奖励能有效提升RL在DAG调度中的性能，为图调度问题提供了新方案。
---

## Abstract
In recent years, many studies proposed to generate solutions for Directed Acyclic Graph (DAG) scheduling problem in one shot by combining reinforcement learning and list scheduling heuristic. However, these existing methods suffer from biased estimation of sampling probabilities and inefficient guidance in training, due to redundant comparisons among node priorities and the sparse reward challenge. To address these issues, we analyze of the limitations of these existing methods, and propose a novel one-shot DAG scheduling method with comparability identification and dense reward signal, based on the policy gradient framework. In our method, a comparable antichain identification mechanism is proposed to eliminate the problem of redundant nodewise priority comparison. We also propose a dense reward signal for node level decision-making optimization in training, effectively addressing the sparse reward challenge. The experimental results show that the proposed method can yield superior results of scheduling objectives compared to other learning-based DAG scheduling methods.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

有向无环图（DAG）调度问题是典型的 NP-hard 组合优化问题，在云计算、制造流程等领域广泛应用。近年来，将强化学习（RL）与列表调度启发式结合的一步式（one-shot）方法受到关注，这些方法通过单次前向传播生成节点优先级列表，从而得到调度方案。然而，现有方法存在两个关键缺陷：

- **冗余节点优先级比较**：在生成优先级列表时，方法会为所有节点对进行两两比较，但位于同一路径上的节点相对顺序实际上由拓扑约束决定，比较是多余的。这种冗余导致采样概率估计有偏、策略梯度方差高。
- **稀疏奖励问题**：一步式方法仅在完整调度后给出一个全局奖励信号，无法为每个节点的局部决策提供有效指导，导致训练效率低、易陷入局部最优。

本文旨在同时解决上述两个问题，提出一种基于策略梯度的新型一步式 DAG 调度方法。

### 2. 论文提出的方法论

#### 核心思想
- 利用 DAG 的拓扑排序过程，在每个调度步骤中，**只对入度为 0 的节点集合（即一个反链）内进行优先级比较和采样**，因为只有这些节点之间的相对优先级才会影响最终执行顺序。这类节点对称为“可比较节点对”，其集合称为“可比较反链”。通过这种机制消除冗余比较。
- 为每个节点引入**密集奖励**：在调度模拟过程中，记录每个节点完成时的部分目标成本（如当前 makespan），并与全局成本做差，再减去一个启发式基线（如 HEFT 的对应值）得到优势函数，从而提供节点级别的精细反馈。

#### 关键技术细节
1. **可比较反链识别**：在每次拓扑排序步骤，当前入度为 0 的节点集合 `V_in=0_t` 构成可比较反链。只在此集合内执行 softmax 操作计算节点被选中的概率：
   \[
   p_\theta(v_{\pi_\theta}(t) | S_{t-1}) = \frac{\exp(\text{logits}_\theta(v_{\pi_\theta}(t)))}{\sum_{v \in V_t^{\text{in}=0}} \exp(\text{logits}_\theta(v))}
   \]
   这保证了采样概率只反映真正影响调度的比较。

2. **密集奖励**：对于调度序列中的第 t 个节点，定义：
   \[
   R_t = C(\text{Solution}(G;\theta)) - C(S_t(G;\theta))
   \]
   其中 \(C(S_t)\) 是调度完前 t 个节点时的部分目标值。进一步减去启发式基线（如 HEFT 在对应节点完成时的成本）得到优势函数 \(A_t\)，并做批归一化。

3. **策略梯度**：将每个节点的选择视为一步动作，梯度表示为：
   \[
   \nabla_\theta J(\theta) = \frac{1}{B} \frac{1}{n} \sum_{j=1}^B \sum_{t=1}^n \nabla_\theta \log p_\theta(v_{\pi_\theta^{(j)}}(t) | S_{t-1}) \cdot A_t^{\text{normalized}}
   \]

- 使用 Graphormer 作为 GNN 编码器，MLP 作为策略网络，引入 Gumbel 扰动进行采样。

### 3. 实验设计

#### 数据集 / 场景
- **Pegasus**：科学工作流调度，异构多处理器环境，含 SIPHT、LIGO、GENOME 等子数据集，节点规模 100~1000。
- **TPC-H**：同构单处理器环境，子 DAG 数 50/100/150。
- **JSSP**：作业车间调度问题（DAG 特例），规模如 20×10、20×20、30×10、30×20。

#### Benchmark 与对比方法
- 启发式基线：HEFT（Pegasus）、STF（TPC-H）、SPT（JSSP）。
- 对比方法：
  - Jeon et al. (2023)：SOTA 一步式 RL 方法。
  - POMO-DAG：将经典 POMO 适配到 DAG 调度（增量式构造）。
  - EGS：基于边生成的 DAG 调度方法。
- 消融变体：**Ours w/o CAI**（去掉可比较反链识别）、**Ours w/o DR**（使用稀疏奖励代替密集奖励）。

### 4. 资源与算力

论文明确提及：实验主要在一台配备 **Intel Gold 6226R CPU、256 GB RAM、NVIDIA RTX 3090 (24G GPU)** 的机器上完成。训练最多 1000 个 epoch，batch size 为 16。未详细说明训练总时长，但提供了各方法在测试时的运行时间（秒级）。

### 5. 实验数量与充分性

- **实验数量**：三个主要基准（Pegasus 多个规模、TPC-H 三个规模、JSSP 四个规模）加上消融实验和额外的附录结果（LIGO、GENOME），共约 15 组不同配置的对比结果。
- **充分性**：覆盖了常见应用场景（异构、同构、JSSP），规模从几十到上千节点；消融实验独立验证了 CAI 和 DR 的贡献。但所有结果仅报告单一数值，**未给出多次重复实验的均值与方差**，可能对随机性敏感的 RL 结果说服力稍弱。尽管如此，对比方法也采用相同设置，公平性尚可。

### 6. 论文的主要结论与发现

- 提出的方法在 **大多数场景下优于所有现有方法**，尤其在 Pegasus 大规模（1000 节点）上显著优于 HEFT 和其他 RL 方法。
- 可比较反链识别（CAI）是贡献更大的模块，去掉后性能下降明显；密集奖励（DR）起到“精细调优”作用。
- 在 TPC-H 小图上，CAI 有时无明显优势甚至略差，归因于小图连通性弱，CAI 掩蔽后学习更困难。
- 方法运行时间略长于 Jeon et al.，但远短于 POMO-DAG 和 EGS，效率可接受。

### 7. 优点

- **问题诊断清晰**：明确指出现有一步式方法的两个根本缺陷（冗余比较、稀疏奖励），并给出形式化分析。
- **方案简洁有效**：可比较反链识别基于拓扑排序天然可得，无需额外复杂计算；密集奖励设计直观且与策略梯度自然匹配。
- **实验覆盖全面**：多个不同类型基准，消融实验验证各模块贡献。
- **可解释性提升**：密集奖励使得一步式方法更像 MDP 轨迹，提高了可解释性。

### 8. 不足与局限

- **目标单一**：当前仅优化 makespan，未涉及 deadline、能耗、负载均衡等实际场景中常见的多目标。
- **适用范围**：方法基于列表调度范式，不能直接用于需要同时决策资源分配和排序的复杂问题（需结合其他规则，如 EFT-greedy）。
- **小图效果不稳定**：在 TPC-H 小图及某些简单 JSSP 上，优势不明显甚至略逊于消融变体。
- **缺少统计误差**：未提供多次运行的均值/标准差，在 RL 训练随机性较大的背景下，结论稳健性需进一步验证。
- **运行时间略有增加**：CAI 引入的拓扑排序循环无法 GPU 并行化，在大规模图上时间开销可能增长。

（完）
