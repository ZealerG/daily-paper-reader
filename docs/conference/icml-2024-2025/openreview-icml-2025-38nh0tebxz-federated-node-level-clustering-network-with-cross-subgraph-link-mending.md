---
title: Federated Node-Level Clustering Network with Cross-Subgraph Link Mending
title_zh: 带有跨子图链接修复的联邦节点级聚类网络
authors: "Jingxin Liu, Renda Han, Wenxuan Tu, Haotian Wang, Junlong Wu, Jieren Cheng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=38Nh0TebXZ"
tags: ["query:graph-part"]
score: 8.0
evidence: 联邦节点级聚类网络，修复跨子图链接
tldr: 本文针对联邦图学习中子图划分导致的链接缺失问题，提出FedNCN方法，利用聚类先验知识修复被破坏的跨子图链接，并通过节点级聚类网络提升样本表示质量。实验证明方法能有效缓解缺失链接问题，提高下游任务性能，为联邦场景下的图学习提供了实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1722, \"height\": 723, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1761, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 807, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1778, \"height\": 911, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-38nh0tebxz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1748, \"height\": 937, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1784, \"height\": 1251, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 965, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1762, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1089, \"height\": 650, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1469, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-38nh0tebxz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1726, \"height\": 853, \"label\": \"Table\"}]"
motivation: 联邦图学习中子图划分导致跨子图链接缺失，影响样本表示质量。
method: 提出FedNCN，利用聚类先验知识修复缺失的跨子图链接。
result: 实验表明方法能有效修复链接，提升模型性能。
conclusion: 该工作为联邦图学习中的子图划分问题提供了有效的链接修复方案。
---

## Abstract
Subgraphs of a complete graph are usually distributed across multiple devices and can only be accessed locally because the raw data cannot be directly shared. However, existing node-level federated graph learning suffers from at least one of the following issues: 1) heavily relying on labeled graph samples that are difficult to obtain in real-world applications, and 2) partitioning a complete graph into several subgraphs inevitably causes missing links, leading to sub-optimal sample representations. To solve these issues, we propose a novel $\underline{\text{Fed}}$erated $\underline{\text{N}}$ode-level $\underline{\text{C}}$lustering $\underline{\text{N}}$etwork (FedNCN), which mends the destroyed cross-subgraph links using clustering prior knowledge. Specifically, within each client, we first design an MLP-based projector to implicitly preserve key clustering properties of a subgraph in a denoising learning-like manner, and then upload the resultant clustering signals that are hard to reconstruct for subsequent cross-subgraph links restoration. In the server, we maximize the potential affinity between subgraphs stemming from clustering signals by graph similarity estimation and minimize redundant links via the N-Cut criterion. Moreover, we employ a GNN-based generator to learn consensus prototypes from this mended graph, enabling the MLP-GNN joint-optimized learner to enhance data privacy during data transmission and further promote the local model for better clustering. Extensive experiments demonstrate the superiority of FedNCN.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在联邦图学习中，完整图被划分为多个子图分布在不同客户端，导致大量跨子图链接丢失（缺失比例可超过55%）。同时，现有节点级联邦图学习方法严重依赖标注数据，而在现实场景中标注很难获取。
- **研究动机**：修复因图划分破坏的跨子图链接，并在无监督（无标签）条件下提升节点表示质量和聚类性能。
- **整体含义**：首次提出无监督联邦节点级聚类框架FedNCN，利用聚类先验知识（原型）来修复缺失链接，实现客户端间信息共享，最终提高聚类效果。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过客户端提取聚类信号（硬可重构的聚类属性），上传至服务端；服务端利用这些信号恢复跨子图潜在链接，并学习共识原型，再回传给客户端优化本地模型。
- **关键技术细节**：
  - **本地模型学习**：每个客户端用GNN提取节点嵌入，再经K-means生成聚类原型；选取每个聚类中距原型最近的k%节点，构成样本矩阵B；用高斯噪声生成掩码矩阵R，训练一个MLP投影器使MLP(R)逼近B，实现去噪式学习，上传R和MLP参数而非原始数据。
  - **跨子图链接修复（服务端）**：
    1. 利用上传的R和MLP推断全局样本矩阵$\tilde{R}$；
    2. **簇内链接修复**：将属于同一客户端的同一簇节点组成子图，计算节点相似度（余弦相似度），构建边；
    3. **簇间链接修复**：使用图核（如COS核）计算不同簇子图之间的亲和度矩阵S，据此在跨簇节点间加边，形成全局图$G_\phi$；
    4. **全局结构精炼**：采用改进的N-Cut方法，计算每条跨子图边的贡献度，保留高贡献边，去除冗余边，得到修复图$G_\psi$。
  - **全局知识共享**：在$G_\psi$上训练GNN生成器，最小化重构损失LMSE与聚类损失LKL（KL散度），得到共识原型和GNN参数，再分发给各客户端。
  - **协同学习**：客户端用收到的共识原型初始化聚类中心，用GNN参数初始化本地GNN，继续本地训练。

## 3. 实验设计：数据集、场景、方法对比

- **数据集**：CiteSeer、PubMed、Amazon-Computer、Amazon-Photo、Questions（共5个基准图数据集）。
- **场景**：每个数据集被划分为5、10、20个客户端（子图），模拟不同联邦规模。
- **基准方法**：
  - **第一组**：5种FGL方法（FedSage+、FedPUB、FedTAD、FedGTA、FedIIH），原为监督方法，论文将其调整为无监督版本用于比较；
  - **第二组**：3种经典FL聚合策略（FedAvg、FedProx、FedPer），客户端均使用本文提出的本地模型，保证公平；
  - 另外还与上述5种方法在5%标注数据下的性能进行比较（监督vs无监督对比）。
- **评估指标**：ACC、NMI、ARI、F1（共4个聚类指标）。

## 4. 资源与算力

- **论文明确提到**：所有实验使用PyTorch 2.4.0，单张NVIDIA GeForce RTX 4090 GPU。
- **训练时长**：未明确给出总训练时长，但指出客户端-服务端交互20轮，每轮本地训练10 epochs。
- **算力总结**：单GPU实验，算力规模中等，可复现。

## 5. 实验数量与充分性

- **实验数量**：
  - 主表（表1）：5个数据集 × 3种客户端数 × 6种对比方法 + 本文方法，共约105组实验（含5次重复，标准差报告）；
  - FL聚合策略对比（表2 & 附录表5）：3种聚合策略 + Local + 本文方法，覆盖所有数据集和客户端数；
  - 监督方法对比（图3、图7）：5种方法×3种客户端数×5数据集；
  - 消融实验：CLM和GKS策略消融（图4）、模块消融（附录图9）、图核消融（附录图8）；
  - 超参数分析（图6）：k从1%到20%；
  - 收敛分析（图5）。
- **充分性评价**：实验覆盖了多种数据集、多种客户端数量、多个基线方法和多个消融变体，重复5次取平均和标准差，结果统计充分、客观、公平。但未包含大规模图（如ogbn-products）或非均匀异质划分场景。

## 6. 论文的主要结论与发现

- FedNCN在无监督设置下，在所有数据集和客户端分割数上均显著优于现有FGL方法（提升几十个百分点）。
- 跨子图链接修复策略可有效恢复损坏链接（从44.74%恢复至78.45%），进而提升聚类性能。
- 与监督FGL方法（仅用5%标签）相比，FedNCN仍保持竞争力，证明其无监督优势。
- 超参数k对性能影响显著：k过小导致信息不足，过大引入噪声；存在最优区间（约5%-10%）。
- 不同图核（COS、WL、SP、LT）对最终结果影响较小，表明方法对图核选择不敏感。

## 7. 优点：方法或实验设计上的亮点

- **方法创新性**：首次将无监督聚类与联邦学习结合，解决子图链接缺失问题；利用去噪式MLP投影器保护隐私（上传的信号难以重构原始数据）。
- **隐私保护**：通过上传不可逆的聚类信号（R和MLP参数）而非原始数据或节点嵌入，增强了隐私安全性；客户端和服务端使用不同模型（MLP vs GNN）进一步隔离信息。
- **链接修复机制**：结合簇内修复（基于相似度）和簇间修复（基于图核），并用N-Cut优化结构，设计精巧。
- **实验充分性**：大量对比、消融、超参数分析，重复实验报告标准差，可信度高。
- **代码与可复现性**：提供算法伪代码（算法1-3），细节清晰。

## 8. 不足与局限

- **实验覆盖**：未在更大规模图（如ogb数据集）或真实联邦场景（非独立同分布划分、客户端数据不对称）上测试，泛化性有待验证。
- **应用限制**：需要每个客户端运行K-means选择代表性节点，计算复杂度与客户端数据规模成正比；超参数k需手动调节。
- **偏差风险**：所有客户端子图是从同一完整图划分得到，假设原始图连通；若原始图本身就有孤立节点或极端异质性，修复效果可能下降。
- **安全分析**：虽然声称信号难以重构，但未提供严格隐私证明或攻击实验（如差分隐私、模型反转防御）。
- **与其他隐私保护技术结合**：未探索与差分隐私、安全多方计算等融合，实际部署时隐私保障还可加强。

（完）
