---
title: A Structure-Aware Framework for Learning Device Placements on Computation Graphs
title_zh: 面向计算图设备放置学习的结构感知框架
authors: "Shukai Duan, Heng Ping, Nikos Kanakaris, Xiongye Xiao, Panagiotis Kyriakis, Nesreen K. Ahmed, Peiyu Zhang, Guixiang Ma, Mihai Capotă, Shahin Nazarian, Theodore L. Willke, Paul Bogdan"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=Kzno1r3Xef"
tags: ["query:graph-rl"]
score: 7.0
evidence: 使用策略学习计算图上的设备放置，与图划分相关
tldr: 本文针对计算图设备放置问题，提出一种桥接编码器-放置器和分组器-放置器的框架。通过图粗化、节点表征学习和策略学习，在OpenVINO小图上实现了高效分配。该方法本质上将图节点分配到不同设备，类似于图划分任务，验证了图学习在资源分配中的有效性。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-kzno1r3xef/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-kzno1r3xef/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1400, \"height\": 794, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 601, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1355, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 730, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 705, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-kzno1r3xef/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 942, \"height\": 378, \"label\": \"Table\"}]"
motivation: 现有设备放置方法分为编码器-放置器和分组器-放置器，二者各有优劣且缺乏融合。
method: 提出五步框架：图粗化、节点表征学习、策略学习等，统一两种架构的优势。
result: 在OpenVINO计算图上实现比基线更高的设备分配效率。
conclusion: 该框架为计算图设备放置提供了有效且通用的学习方案。
---

## Abstract
Computation graphs are Directed Acyclic Graphs (DAGs) where the nodes correspond to mathematical operations and are used widely as abstractions in optimizations of neural networks. The device placement problem aims to identify optimal allocations of those nodes to a set of (potentially heterogeneous) devices. Existing approaches rely on two types of architectures known as grouper-placer and encoder-placer, respectively. In this work, we bridge the gap between encoder-placer and grouper-placer techniques and propose a novel framework for the task of device placement, relying on smaller computation graphs extracted from the OpenVINO toolkit. The framework consists of five steps, including graph coarsening, node representation learning and policy optimization. It facilitates end-to-end training and takes into account the DAG nature of the computation graphs. We also propose a model variant, inspired by graph parsing networks and complex network analysis, enabling graph representation learning and jointed, personalized graph partitioning, using an unspecified number of groups. To train the entire framework, we use reinforcement learning using the execution time of the placement as a reward. We demonstrate the flexibility and effectiveness of our approach through multiple experiments with three benchmark models, namely Inception-V3, ResNet, and BERT. The robustness of the proposed framework is also highlighted through an ablation study. The suggested placements improve the inference speed for the benchmark models by up to $58.2\%$ over CPU execution and by up to $60.24\%$ compared to other commonly used baselines.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：计算图（Directed Acyclic Graph, DAG）的**设备放置（Device Placement）**问题——如何将计算图中的每个操作（节点）最优地分配到一组异构设备（如CPU、GPU、NPU）上，以最小化模型推理的**执行时间**。
- **研究动机**：随着基础模型（如BERT）规模增大，计算需求急剧上升，人工手动分配设备耗时且易出错。现有方法分为两类：**分组器-放置器（grouper-placer）**和**编码器-放置器（encoder-placer）**，前者预定义组数（不够灵活），后者忽略图的DAG特性且无法端到端联合训练。
- **整体含义**：本文提出一个**结构感知框架（HSDAG）**，融合两类方法的优点，在OpenVINO生成的较小计算图上实现端到端的图粗化、节点表征学习、分组和策略优化，显著提升推理速度。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：五步流程——（1）将神经网络模型转换为计算图（使用OpenVINO）；（2）提取初始节点特征（局部结构、全局分形维数、位置编码、输出形状等）；（3）**联合学习节点嵌入和分组**：利用**图解析网络（Graph Parsing Network, GPN）**，通过GNN编码节点，计算边分数，自适应地将图划分为**数量不固定的组**（无需预设组数）；（4）设备分配：对粗化图的每个组用MLP分配设备，再通过分配矩阵映射回原图；（5）**强化学习训练**：以推理时间的倒数作为奖励，使用REINFORCE算法和Adam优化器更新参数。
- **关键技术细节**：
  - 特征提取：节点类型、入度/出度（one-hot）、分形维数D(v)、拓扑序位置编码（正弦/余弦）、输出形状张量。
  - 图解析网络：GNN编码 → 边分数矩阵S = sigmoid(MLP(z_v ⊙ z_u)) → 保留每个节点最高分边形成分组 → 生成分配矩阵X和粗化图。
  - 强化学习：奖励r = 1/执行时间；梯度∇θJ(θ) ≈ -∑γ^i·r·∇θ log p(P|G')；每x步更新一次。
- **公式**：主要涉及分形维数计算（式4）、位置编码（式5）、GCN卷积（式6）、边分数（式7）、目标函数（式12）和梯度（式14）。

### 3. 实验设计：数据集、Benchmark、对比方法

- **数据集/场景**：三个基准神经网络模型——**Inception-V3**（图像分类）、**ResNet-50**（图像分类）、**BERT-base uncased**（语言模型）。计算图通过OpenVINO工具包生成并进一步粗化。
- **Benchmark**：执行时间（秒）和相对CPU-only的加速比。
- **对比方法**：
  - CPU-only、GPU-only（单设备全图执行）
  - OpenVINO-CPU、OpenVINO-GPU（让OpenVINO自动选择设备）
  - **Placeto**（基于GNN的RL方法，可迁移策略）
  - **RNN-based**（序列到序列LSTM+注意力机制的RL方法）
- **硬件**：CPU（12th Gen i9-12900K）、iGPU（Intel UHD Graphics 770）、dGPU（Intel Data Center GPU Flex 170）。

### 4. 资源与算力

- **明确信息**：文中未报告训练总时长、GPU具体使用数量、能耗等详细算力开销。仅提及硬件配置、OpenVINO版本（2023.3.0）、PyTorch Geometric框架。在运行时复杂度对比（表5）中给出了各方法在三个模型上的训练时长（单位秒），但未说明运行该训练所需的GPU或CPU资源。
- **结论**：**未充分披露**完整的训练资源需求（如GPU型号数量、训练轮数、总耗时），但给出了硬件环境。

### 5. 实验数量与充分性

- **实验组数**：
  - 主性能对比（表2）：3个模型 × 7种方法（包括HSDAG） = 21个结果，每个结果测量10次取后5次平均。
  - 消融研究（表3）：3个模型 × 4种变体（原始、无输出形状、无节点ID、无图结构特征） = 12个结果。
  - 下游任务验证：Inception-V3和ResNet的分类准确率，BERT的MSE/余弦相似度/L2距离（表4）。
  - 运行时复杂度（表5）：3个模型 × 3种方法（Placeto、RNN、HSDAG）。
- **充分性评价**：**比较充分**，覆盖了主流基线、重要特征消融、下游任务验证和计算效率。但**缺乏误差棒和统计显著性检验**（如置信区间、p值），且测量次数较少（10次取后5次），可能受环境波动影响。同时，基线方法因原作者未开源，由作者自行复现，存在实现偏差风险。

### 6. 论文的主要结论与发现

- **HSDAG在三个基准模型上均显著优于对比方法**：推理速度相比CPU-only提升17.9%（Inception-V3）、52.1%（ResNet）、58.2%（BERT）；相比Placeto、RNN-based等基线也有明显优势（最高60.24%）。
- **消融实验表明**：输出形状特征和节点ID（拓扑序）对性能影响最大（删除后加速比从17.9%降至8.59%），图结构特征次之。
- **下游任务性能不受影响**：各模型在不同放置策略下的分类精度或输出嵌入相似度几乎一致。
- **框架具有灵活性和鲁棒性**：支持端到端训练，可自适应学习分组数，融合分组器和编码器两种架构优势。

### 7. 优点

- **方法论创新**：首次在设备放置中**联合学习图表示和分组**，且分组数可学习（无需预设），桥接了grouper-placer和encoder-placer。
- **特征工程丰富**：引入分形维数、位置编码等结构特征，提升模型对图拓扑的理解。
- **端到端训练**：从图粗化到策略优化完全可微，使用强化学习直接优化推理时间。
- **实用性**：基于OpenVINO的**较小计算图**，降低复杂度，收敛更快；实验代码已开源。
- **全面评估**：包含主实验、消融、下游任务和运行时复杂度对比，实验设计较充分。

### 8. 不足与局限

- **实验环境控制不足**：未考虑温度等环境变化对延迟测量的影响；训练时CPU同时用于实验和策略，可能引入干扰。
- **硬件覆盖有限**：未考虑iGPU（认为其总是较慢），且仅使用Intel设备，未测试NVIDIA等生态。
- **基线复现偏差**：Placeto和RNN-based的代码未公开，作者自行复现，可能未达到原论文最佳性能，导致对比不公平。
- **统计严谨性缺失**：没有报告误差棒、置信区间或多次运行的标准差；仅10次测量取后5次平均，样本量较少。
- **强化学习局限性**：奖励依赖实际推理延迟，存在噪声，且未探索其他奖励结构（如增量奖励）。
- **可扩展性**：目前只测试到1009个节点的BERT，未验证更大模型（如GPT-3）或更复杂硬件拓扑下的性能。

（完）
