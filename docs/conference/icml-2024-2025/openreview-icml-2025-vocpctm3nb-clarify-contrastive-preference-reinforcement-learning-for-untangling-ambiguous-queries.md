---
title: "CLARIFY: Contrastive Preference Reinforcement Learning for Untangling Ambiguous Queries"
title_zh: CLARIFY：对比偏好强化学习用于解开模糊查询
authors: "Ni Mu, Hao Hu, Xiao Hu, Yiqin Yang, Bo XU, Qing-Shan Jia"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vOCPctm3nb"
tags: ["query:graph-part"]
score: 8.0
evidence: 偏好强化学习方法解决模糊查询问题
tldr: 本文提出CLARIFY方法，一种离线偏好强化学习算法，通过对比学习构建轨迹嵌入空间以区分模糊片段，从而提升偏好标签的质量和样本效率。实验证明其在偏好学习任务上显著优于现有基线，为实际偏好标注场景提供了有效解决方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1579, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1553, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1586, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 831, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 724, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1694, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vocpctm3nb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1641, \"height\": 747, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1783, \"height\": 555, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 668, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 833, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 648, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 888, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 434, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1050, \"height\": 1036, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vocpctm3nb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1076, \"height\": 1828, \"label\": \"Table\"}]"
motivation: 人类在偏好标注中难以区分相似片段，降低标签效率。
method: 提出对比学习框架，学习轨迹嵌入空间，使清晰片段分离以选择更明确的查询。
result: 实验表明CLARIFY在偏好学习任务中显著优于基线方法。
conclusion: 该工作解决了偏好强化学习中模糊反馈的问题，提高了实际可用性。
---

## Abstract
Preference-based reinforcement learning (PbRL) bypasses explicit reward engineering by inferring reward functions from human preference comparisons, enabling better alignment with human intentions. However, humans often struggle to label a clear preference between similar segments, reducing label efficiency and limiting PbRL’s real-world applicability. To address this, we propose an offline PbRL method: Contrastive LeArning for ResolvIng Ambiguous Feedback (CLARIFY), which learns a trajectory embedding space that incorporates preference information, ensuring clearly distinguished segments are spaced apart, thus facilitating the selection of more unambiguous queries. Extensive experiments demonstrate that CLARIFY outperforms baselines in both non-ideal teachers and real human feedback settings. Our approach not only selects more distinguished queries but also learns meaningful trajectory embeddings.

---

## 论文详细总结（自动生成）

# CLARIFY 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：在偏好强化学习（PbRL）中，人类标注者难以区分高度相似的轨迹片段，导致偏好标签出现“模糊查询”（ambiguous queries），即标注者无法给出明确的偏好信号。这降低了标签效率，限制了PbRL在真实场景中的实用性。
- **背景**：传统PbRL方法依赖人工偏好比较来推断奖励函数，但面对相似片段时人类判断的不确定性会引入噪声，甚至跳过标注。现有离线PbRL方法（如OPRL、PT等）未针对此问题进行专门优化。
- **目标**：提出一种离线PbRL方法，通过选择更清晰的查询（unambiguous queries）来提高标签效率，使人类标注更容易，从而提升策略性能。

## 2. 方法论

### 核心思想
利用对比学习构建一个轨迹嵌入空间，在该空间中，清晰可区分的片段对距离较远，而模糊片段对距离较近。基于该嵌入空间，通过拒绝采样（reject sampling）选择更具区分性的查询，减少模糊标签的引入。

### 关键技术细节
- **轨迹编码器**：使用双向决策变换器（Bi-directional Decision Transformer, BDT）作为编码器 \( z = f_\phi(\tau) \)，将任意长度轨迹映射为固定维度的嵌入向量。
- **两种对比损失**：
  - **模糊损失** \( \mathcal{L}_{\text{amb}} \)：最大化清晰区分片段对的距离，同时最小化模糊片段对的距离。直接优化区分性。
  - **四边形损失** \( \mathcal{L}_{\text{quad}} \)：利用偏好关系，对每对清晰查询构建四边形关系，使“好”片段之间和“差”片段之间的距离之和小于“好-差”之间的距离。该损失扩大了数据量（从 \( O(n) \) 到 \( O(n^2) \)），缓解过拟合，并防止嵌入空间塌缩。
- **正则项**：对嵌入向量的L2范数施加约束（\( \mathcal{L}_{\text{norm}} \)），防止嵌入无限增大或塌缩到原点。
- **总损失**：\( \mathcal{L} = \mathcal{L}_{\text{recon}} + \lambda_{\text{amb}} \mathcal{L}_{\text{amb}} + \lambda_{\text{quad}} \mathcal{L}_{\text{quad}} + \lambda_{\text{norm}} \mathcal{L}_{\text{norm}} \)，其中 \( \mathcal{L}_{\text{recon}} \) 为BDT的重构损失（预测动作）。
- **查询选择**：基于嵌入距离 \( d_{\text{emb}} \) 的分布，使用拒绝采样。先估计清晰和模糊片段对的密度函数 \( \rho_{\text{clr}} \) 和 \( \rho_{\text{amb}} \)，构建新分布 \( \rho(d_{\text{emb}}) \) 强调清晰对，然后乘以原始分布得到采样分布 \( q(d_{\text{emb}}) \)，提高选中清晰查询的概率。对于拒绝采样后剩余的查询，采用最大不一致性（maximum disagreement）策略（类似OPRL）。
- **算法流程**：先随机采样一批查询，预训练编码器和奖励模型；然后基于嵌入空间选择查询，更新偏好数据集和奖励模型；最后用IQL进行离线策略学习。

### 理论分析（摘要）
- 命题1：在最优模糊损失下，清晰区分片段对的最小距离严格大于模糊片段对的最大距离，存在正间隔 \( \delta \)。
- 命题2：四边形损失最小化后，正负样本在嵌入空间中线性可分，且存在分类超平面和间隔 \( \eta \)。

## 3. 实验设计

- **数据集与场景**：使用Choi等人(2024)提供的离线数据集，包含7个Metaworld任务（box-close, dial-turn, drawer-open, handle-pull-side, hammer, peg-insert-side, sweep-into）和2个DMControl任务（cheetah-run, walker-walk）。这些任务被证明对奖励学习敏感，避免D4RL中“生存本能”问题。
- **基准与非理想教师设计**：采用脚本化教师，当片段间真实奖励和差值小于阈值 \( \epsilon H \cdot r_{\text{avg}} \) 时，教师跳过查询（标记为 no cop）。\( \epsilon \) 称为跳过率（skip rate），实验中采用 0.5 和 0.7。此外还进行了真实人类标注实验。
- **对比方法**：Markovian Reward (MR)、Preference Transformer (PT)、OPRL、OPPO、LiRE，以及带有真实奖励的IQL上界。所有方法均使用IQL作为下游离线RL算法。

## 4. 资源与算力

- **明确说明**：论文中未明确提及使用的GPU型号、数量及训练时长。仅在附录C.2中列出了一些超参数（如梯度步数 n_init=20000, n_emb=2000, n_reward=50, 总反馈数 1000/500/200 等），但无具体算力开销。因此，无法总结资源与算力细节。

## 5. 实验数量与充分性

- **实验组数**：
  - 表1：2种skip率 × 9个任务 × 6个随机种子，每种方法得到180个结果（不含IQL上界），对比了6种方法。
  - 表2：不同查询数量（100,500,1000,2000）下的性能对比，2个任务。
  - 表3：清晰查询比例对比，4个任务。
  - 表4：查询选择方法消融，2个任务。
  - 表5：真实人类实验（walker-walk），3个种子。
  - 表6：损失函数消融，2个任务。
  - 图3：嵌入空间可视化（4个任务）。
  - 图4-5：人类标注清晰度和准确性（3个任务，各20个查询×3种子）。
  - 附录还有超参数鲁棒性可视化（图6）。
- **充分性与公平性**：实验覆盖了多种任务、跳过率、查询数量，并进行了消融和人类验证。所有对比方法使用相同离线数据集和超参数搜索（附录C.2），且报告了6个种子的均值和标准差，具有统计意义。公平性较好。

## 6. 主要结论与发现

- CLARIFY在大多数任务上显著优于所有基线，尤其是在高跳过率（0.7）下仍保持较好性能。
- CLARIFY选择的查询具有更高的清晰度（人类标注时更少跳过、更高准确率）。
- 学习到的嵌入空间能有效将高回报轨迹与低回报轨迹分开，形成有意义的聚类。
- 四边形损失和模糊损失共同作用不可或缺，单独使用任一损失性能下降。
- 在真实人类标注实验中，CLARIFY同样优于OPRL，验证了其实际应用潜力。

## 7. 优点

- **方法创新**：将对比学习引入离线PbRL的查询选择，提出两种互补的对比损失，同时处理模糊性和偏好关系。
- **理论支撑**：给出了边际间隔和线性可分性的理论证明，增强了方法的可信度。
- **实验全面**：包括脚本教师和真实人类实验，覆盖多种任务和超参数，消融充分。
- **实用性**：通过选择清晰查询提高标签效率，减少了人类标注负担，可用于RLHF等现实场景。
- **嵌入可解释性**：可视化表明嵌入空间与轨迹性能高度相关，有助于理解。

## 8. 不足与局限

- **算力资源未报告**：未说明训练所需GPU型号、数量、时间，难以评估计算成本。
- **离线设置限制**：方法针对离线PbRL设计，在线设置（如PEBBLE）中的模糊查询问题未解决（虽有前人工作S-EPOA，但不可直接迁移）。
- **预训练开销**：需要先进行20000步的编码器预训练（n_init），可能增加前期时间成本。
- **人类实验偏差**：人类标注者为作者本人，可能存在主观偏差；且仅在一个任务（walker-walk）上进行了真实人类对比实验，泛化性需更多验证。
- **对数据集质量依赖**：实验中对多个任务提高了数据集质量（表7），以确保方法不全部失败，表明方法在低质量数据下可能不稳定。
- **未讨论标签噪声**：虽然考虑了模糊查询，但未考虑人类标注中的其他非理性行为（如随机错误、偏见）。

（完）
