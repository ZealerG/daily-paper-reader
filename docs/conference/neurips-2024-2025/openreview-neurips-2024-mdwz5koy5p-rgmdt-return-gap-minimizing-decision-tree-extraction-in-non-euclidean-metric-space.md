---
title: "RGMDT: Return-Gap-Minimizing Decision Tree Extraction in Non-Euclidean Metric Space"
title_zh: RGMDT：非欧几里得度量空间中最小化返回间隙的决策树提取
authors: "Jingdi Chen, Hanhan Zhou, Yongsheng Mei, Carlee Joe-Wong, Gina Adam, Nathaniel D. Bastian, Tian Lan"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=mdWz5koY5p"
tags: ["query:graph-part"]
score: 9.0
evidence: 深度强化学习策略决策树提取
tldr: 该文针对深度强化学习策略黑箱不可解释的问题，提出一种基于非欧几里得度量空间的决策树提取方法RGMDT。该方法在单智能体基础上扩展至多智能体场景，并建立了专家策略与提取决策树策略之间的返回间隙上界。实验证明提取的决策树策略在保持较高回报的同时具有可解释性。该工作推动了可解释强化学习的发展并提供了理论保证。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1405, \"height\": 797, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 577, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1397, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1250, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1277, \"height\": 1228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1392, \"height\": 1312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1415, \"height\": 1145, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1429, \"height\": 1487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-mdwz5koy5p/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 1087, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdwz5koy5p/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdwz5koy5p/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1250, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-mdwz5koy5p/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1212, \"height\": 731, \"label\": \"Table\"}]"
motivation: 深度强化学习策略黑箱不可解释限制了实际应用。
method: 提出RGMDT方法，在非欧几里得度量空间中通过最小化返回间隙提取决策树策略。
result: 提取的决策树策略具备可解释性且与专家策略的返回间隙有理论保证。
conclusion: 为可解释强化学习提供了新的理论框架和方法。
---

## Abstract
Deep Reinforcement Learning (DRL) algorithms have achieved great success in solving many challenging tasks while their black-box nature hinders interpretability and real-world applicability, making it difficult for human experts to interpret and understand DRL policies. 
Existing works on interpretable reinforcement learning have shown promise in extracting decision tree (DT) based policies from DRL policies with most focus on the single-agent settings while prior attempts to introduce DT policies in multi-agent scenarios mainly focus on heuristic designs which do not provide any quantitative guarantees on the expected return.
In this paper, we establish an upper bound on the return gap between the oracle expert policy and an optimal decision tree policy. This enables us to recast the DT extraction problem into a novel non-euclidean clustering problem over the local observation and action values space of each agent, with action values as cluster labels and the upper bound on the return gap as clustering loss.
Both the algorithm and the upper bound are extended to multi-agent decentralized DT extractions by an iteratively-grow-DT procedure guided by an action-value function conditioned on the current DTs of other agents. Further, we propose the Return-Gap-Minimization Decision Tree (RGMDT) algorithm, which is a surprisingly simple design and is integrated with reinforcement learning through the utilization of a novel Regularized Information Maximization loss. Evaluations on tasks like D4RL show that RGMDT significantly outperforms heuristic DT-based baselines and can achieve nearly optimal returns under given DT complexity constraints (e.g., maximum number of DT nodes).

---

## 论文详细总结（自动生成）

# 论文总结：RGMDT: Return-Gap-Minimizing Decision Tree Extraction in Non-Euclidean Metric Space

## 1. 核心问题与整体含义（研究动机和背景）
- **问题背景**：深度强化学习（DRL）在复杂任务中表现优异，但其深度神经网络的“黑箱”特性导致决策过程难以解释，阻碍了在医疗、航空等安全关键领域的实际应用。
- **现有不足**：已有工作尝试从DRL中提取决策树（DT）策略以增强可解释性，但大多集中在单智能体场景；多智能体场景的尝试（如MAVIPER）缺乏严格的性能保证（return gap），且往往采用启发式设计。
- **核心目标**：提出一种理论上有界的、可扩展的多智能体决策树提取方法，在保证可解释性的同时，使DT策略的期望回报尽可能接近原始DRL专家策略。

## 2. 方法论
### 核心思想
- **重新诠释DT构建**：将决策树提取问题转化为**非欧几里得聚类问题**。每个决策路径对应一个观测子集和一个叶节点动作，因此构建DT等价于迭代地将观测聚类成不同决策路径，并以动作值作为标签。
- **返回间隙上界**：利用动作值函数 \(Q(o,a)\) 导出专家策略 \(\pi^*\) 与DT策略 \(T^L\) 之间的期望回报差的上界（Thm.4.2/4.4），并将该上界作为聚类损失。
- **迭代增长过程**：在多智能体场景中，每个智能体的DT构建依赖于其他智能体当前的DT，通过交替更新动作值函数（条件化于其余智能体的DT）逐步生长DT，直至达到复杂度约束。

### 关键技术细节
- **非欧几里得度量空间**：观测空间 \(\Omega_j\) 以余弦距离 \(D_{\cos}\) 构成度量空间（Lemma 4.3）。
- **聚类标签生成**：使用深度神经网络 \(g_{\xi_j}(o_j)\) 生成标签，优化一个**正则化信息最大化（RIM）损失**，包含：
    - 局部保持聚类损失（用余弦距离近邻促进同类聚合）；
    - 互信息损失（平衡聚类大小与清晰度）。
- **SVM分裂**：在每个非叶节点，利用SVM寻找最优超平面 \(w\cdot x - p=0\) 实现分裂，而非传统CART的增益最大化。
- **迭代增长算法**：算法1（NEC）生成聚类标签；算法2（RGMDT）交替为每个智能体生长一层DT，共 \(\log_2(L)+1\) 次迭代。

## 3. 实验设计
### 数据集/场景
1. **迷宫任务**：单智能体（简单/中等/困难三级难度），基于MuJoCo构建，需导航至目标并避开障碍。
2. **D4RL**：Hopper和Half Cheetah环境，训练样本量分80,000和800,000，DT节点数分40和64。
3. **多智能体捕食者-猎物任务**：2个和3个智能体，需协作到达目标。

### Benchmark与对比方法
- **单任务树模型**：CART
- **装袋/集成树**：Random Forest (RF), Extra Trees (ET)
- **提升树**：Gradient Boosting Decision Tree (GBDT)
- **多智能体基线**：MAVIPER
- 所有基线均通过模仿预训练DRL策略的行为直接训练。

### 评估指标
- 任务完成步数（归一化）
- 平均回合回报
- D4RL中回报值及其标准差

## 4. 资源与算力
- **硬件**：Ubuntu 20.04，Intel Core i9-7290K CPU (4.4 GHz)，4× NVIDIA 2080Ti GPU，256 GB RAM。
- **软件**：Python 3.8，NumPy 1.22.3，Pandas 2.0.3，MuJoCo，OpenAI Gym。
- **训练时长**：论文未明确报告单次训练时长或总GPU小时数，仅提到使用4张2080Ti。

## 5. 实验数量与充分性
### 实验组数
- 单智能体迷宫：3种难度 × 5次随机种子，每种展示步数和回报曲线。
- D4RL：2个环境 × 2种样本量 × 2种节点数，每种5次？数据表显示标准差。
- 多智能体任务：2智能体（2/4/8节点），3智能体（2/4/8节点），每种多个种子？图3显示均值和误差带。
- 消融实验：表2涉及5种变体（移除SVM→替换为CART/ET/RF/GBDT，移除非欧几里得聚类，移除迭代增长过程），每个条件有平均回报和标准差。

### 充分性与公平性
- **充分性**：涵盖单/多智能体、离散/连续状态、不同复杂度、不同节点数、不同样本量，以及关键组件消融，比较全面。
- **公平性**：所有基线均使用相同训练数据和预训练DRL策略；重复3-5次取均值标准差。但未在更复杂的多智能体场景（如星际争霸、拉网战）测试，也未与更多可解释RL方法（如软决策树、可微分DT）对比。

## 6. 主要结论与发现
1. **RGMDT显著优于所有基线**，尤其在DT节点数极少时（2/4节点）仍能完成任务，而所有基线均失败。
2. **性能随叶节点数增加而提升**，接近专家DRL策略水平（4节点以上即达近最优）。
3. **理论保证成立**：返回间隙随平均余弦距离 \(\epsilon\) 减小而降低，与Thm.4.4一致。
4. **数据效率高**：在D4RL上，即使样本量减少10倍（80,000 vs 800,000），RGMDT仍优于基线，表明其更鲁棒、噪声影响小。
5. **消融实验**：非欧几里得聚类的余弦距离、迭代增长过程、SVM分裂均为关键组件，缺失任一会导致性能大幅下降（甚至任务失败）。

## 7. 优点
- **理论贡献**：首次为多智能体决策树提取提供**闭式返回间隙上界**，并将其转化为可优化的聚类损失。
- **方法创新**：将非欧几里得聚类（余弦距离）与迭代增长过程结合，有效处理多智能体相互依赖；RIM损失函数简洁高效。
- **可解释性保持**：提取的DT规模小（4-32叶节点），天然可解释，且保持接近原始DRL的性能。
- **实验验证充分**：单/多智能体、连续/离散任务、不同复杂度、消融实验均有力地支撑了主要主张。

## 8. 不足与局限
- **环境覆盖有限**：仅在迷宫和D4RL上进行，未涉及更复杂的大规模多智能体场景（如SMAC、Hanabi）或真实机器人控制。
- **计算开销未详细报告**：未提供训练时间、收敛速度等量化指标，难以评估实际效率。
- **依赖预训练动作值函数**：聚类标签的质量完全依赖于预训练DRL策略的Q值，若Q值不准确则上界可能松弛。
- **连续动作空间需近似**：虽说明可用余弦距离和采样处理连续情况，但未在完全连续动作任务上验证。
- **未与更多可解释方法对比**：如软决策树（soft DT）、可微分DT、基于规则提取的方法等，缺少横向比较。
- **理论假设**：假设观测/动作空间离散有限，对于连续空间需要积分或采样近似，可能引入误差。

（完）
