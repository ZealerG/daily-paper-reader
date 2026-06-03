---
title: "${\\rm E}(3)$-Equivariant Actor-Critic Methods for Cooperative Multi-Agent Reinforcement Learning"
title_zh: 面向合作多智能体强化学习的E(3)等变演员-评论家方法
authors: "Dingyang Chen, Qi Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=yShA4VPYZB"
tags: ["query:graph-part"]
score: 6.0
evidence: 合作多智能体强化学习中的对称性利用
tldr: 本文形式化了一类具有对称性的马尔可夫博弈，并设计了E(3)等变神经网络架构用于合作多智能体强化学习。该方法在多个任务上取得更优性能，验证了利用对称性作为归纳偏置的有效性。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1747, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 573, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 781, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 863, \"height\": 918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 601, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 1239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 859, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1779, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1371, \"height\": 1729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ysha4vpyzb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1412, \"height\": 751, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1682, \"height\": 813, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1565, \"height\": 689, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 889, \"height\": 468, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1397, \"height\": 646, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1711, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1721, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 765, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-ysha4vpyzb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 765, \"height\": 200, \"label\": \"Table\"}]"
motivation: 利用物理世界中的对称性可提升多智能体强化学习的效率和泛化能力。
method: 设计E(3)等变神经网络架构嵌入对称性约束，保证策略等变性。
result: 在合作任务中实现更高的累计奖励和收敛速度。
conclusion: 等变性归纳偏置能有效提升多智能体强化学习的性能。
---

## Abstract
Identification and analysis of symmetrical patterns in the natural world have led to significant discoveries across various scientific fields, such as the formulation of gravitational laws in physics and advancements in the study of chemical structures. In this paper, we focus on exploiting Euclidean symmetries inherent in certain cooperative multi-agent reinforcement learning (MARL) problems and prevalent in many applications. We begin by formally characterizing a subclass of Markov games with a general notion of symmetries that admits the existence of symmetric optimal values and policies. Motivated by these properties, we design neural network architectures with symmetric constraints embedded as an inductive bias for multi-agent actor-critic methods. This inductive bias results in superior performance in various cooperative MARL benchmarks and impressive generalization capabilities such as zero-shot learning and transfer learning in unseen scenarios with repeated symmetric patterns.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
合作多智能体强化学习中的对称性利用。

### 2. 核心内容
本文形式化了一类具有对称性的马尔可夫博弈，并设计了E(3)等变神经网络架构用于合作多智能体强化学习。该方法在多个任务上取得更优性能，验证了利用对称性作为归纳偏置的有效性。

### 3. 对应检索需求
multi agent parallel decision making with reinforcement learning。

### 4. 来源与原文
- Source：ICML-2024-Public
- OpenReview：[https://openreview.net/forum?id=yShA4VPYZB](https://openreview.net/forum?id=yShA4VPYZB)
