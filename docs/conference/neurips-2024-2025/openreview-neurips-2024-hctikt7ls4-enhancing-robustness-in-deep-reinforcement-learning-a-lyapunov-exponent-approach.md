---
title: "Enhancing Robustness in Deep Reinforcement Learning: A Lyapunov Exponent Approach"
title_zh: 基于李雅普诺夫指数的深度强化学习鲁棒性增强
authors: "Rory Young, Nicolas Pugeault"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=HCTikT7LS4"
tags: ["query:graph-part"]
score: 9.0
evidence: 基于李雅普诺夫指数分析深度强化学习鲁棒性
tldr: 该文发现深度强化学习策略对微小状态扰动具有确定性混沌行为，导致鲁棒性不足。为此提出利用李雅普诺夫指数分析策略的混沌特性，并设计相应的鲁棒性增强方法。实验表明该方法显著提升了策略对观测噪声和对抗攻击的抵抗能力。该工作为提高强化学习的实际部署可靠性提供了新思路。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1381, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1388, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1401, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1202, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1414, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1398, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1418, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1384, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1410, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-hctikt7ls4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1413, \"height\": 702, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 363, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 992, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 1547, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 596, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 478, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 597, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-hctikt7ls4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 735, \"label\": \"Table\"}]"
motivation: 深度强化学习策略对观测噪声和对抗攻击不鲁棒。
method: 引入李雅普诺夫指数量化策略的混沌程度并指导鲁棒性训练。
result: 在连续控制任务中显著提升策略鲁棒性。
conclusion: 揭示了DRL策略的混沌本质并提出有效的鲁棒增强方案。
---

## Abstract
Deep reinforcement learning agents achieve state-of-the-art performance in a wide range of simulated control tasks. However, successful applications to real-world problems remain limited. One reason for this dichotomy is because the learnt policies are not robust to observation noise or adversarial attacks. In this paper, we investigate the robustness of deep RL policies to a single small state perturbation in deterministic continuous control tasks. We demonstrate that RL policies can be deterministically chaotic, as small perturbations to the system state have a large impact on subsequent state and reward trajectories. This unstable non-linear behaviour has two consequences: first, inaccuracies in sensor readings, or adversarial attacks, can cause significant performance degradation; second, even policies that show robust performance in terms of rewards may have unpredictable behaviour in practice. These two facets of chaos in RL policies drastically restrict the application of deep RL to real-world problems. To address this issue, we propose an improvement on the successful Dreamer V3 architecture, implementing Maximal Lyapunov Exponent regularisation. This new approach reduces the chaotic state dynamics, rendering the learnt policies more resilient to sensor noise or adversarial attacks and thereby improving the suitability of deep reinforcement learning for real-world applications.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
深度强化学习（DRL）在模拟控制任务中表现优异，但在现实世界中部署受限，主要原因之一是学习到的策略对观测噪声和对抗攻击缺乏鲁棒性。本文发现，即使在确定性连续控制任务中，**DRL策略对单一微小状态扰动也会产生混沌行为**——初始状态的微小差异会导致后续状态和奖励轨迹指数级发散。这种混沌动力学带来两个后果：① 传感器误差或对抗攻击可显著降低性能；② 即使平均奖励较高，策略的实际行为仍不可预测。因此，提升策略对局部扰动的稳定性是DRL迈向实际应用的关键。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
**核心思想**：引入**最大李雅普诺夫指数（Maximal Lyapunov Exponent, MLE）正则化**，在策略优化过程中约束状态轨迹的混沌程度，从而提高鲁棒性。

**关键技术细节**：
- 基于Dreamer V3架构，利用其循环状态空间模型（RSSM）预测未来轨迹。
- 通过RSSM的**随机性**，从同一初始状态重复采样 \(L\) 条未来轨迹（\(L=3\)），计算每个时间步状态集合 \(\mathcal{S}_t\) 和隐状态集合 \(\mathcal{H}_t\) 的方差，作为**局部状态散度**的估计。
- 将方差项作为正则项加入策略损失，鼓励策略产生更稳定的轨迹。

**公式**：
- 原始Dreamer V3策略损失：  
  \[
  L_{\text{Dr3}}(\theta) = -\sum_{t=1}^{T} \left[ \operatorname{sg}\left(\frac{R_t^\lambda - v_\phi(s_t)}{\max(1, S)}\right) \log \pi_\theta(a_t|s_t) + \eta H[\pi_\theta(a_t|s_t)] \right]
  \]
- MLE正则项：  
  \[
  L_{\lambda_1}(\theta) = \sum_{t=1}^{T} \left[ \operatorname{Var}_L(\mathcal{S}_t) + \operatorname{Var}_L(\mathcal{H}_t) \right]
  \]
- 总策略损失：  
  \[
  L_{\text{Policy}}(\theta) = L_{\text{Dr3}}(\theta) + L_{\lambda_1}(\theta)
  \]

**算法流程**（文字描述）：
1. 从当前状态 \(s\) 和隐状态 \(h\) 出发，编码得到 \(L\) 个随机表征 \(z\)。
2. 对每个时间步 \(t=1..T\)：
   - 策略生成 \(L\) 个动作 \(a\)；
   - 更新 \(L\) 个隐状态 \(h\)；
   - 更新 \(L\) 个随机表征 \(z\)；
   - 解码预测 \(L\) 个状态 \(s\)；
   - 累加当前步状态和隐状态的方差。
3. 返回累加的方差作为正则损失。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法
- **场景**：DeepMind Control Suite 中的7个确定性连续控制任务：
  - 简单低维：Pointmass Easy, Cartpole Balance, Cartpole Swingup
  - 复杂高维：Walker Stand, Walker Walk, Walker Run, Cheetah Run
- **基准方法**：
  - 无动作基线（None）
  - Soft Actor-Critic (SAC)
  - Twin Delayed DDPG (TD3)
  - Dreamer V3 (DR3)
  - 本文方法：Dreamer V3 + MLE 正则化（MLE DR3）
- **评估指标**：
  - 平均总奖励（80个episode，每个1000步）
  - 状态MLE和状态SLE（20个初始状态）
  - 奖励MLE
  - 抗噪性能：添加高斯噪声 \(\mathcal{N}(0, \sigma)\)，\(\sigma \in [0,1]\)

### 4. 资源与算力
论文明确提到使用的硬件：
- CPU：Intel Core i7-8700
- GPU：Nvidia RTX 2080 Ti
- 内存：32GB RAM
- 训练步数：SAC/TD3 为 \(5\times10^6\) 步，Dreamer V3 为 \(10^6\) 步。
- 未明确说明总训练时长、模型参数数量或具体计算成本，仅提及“保持与Dreamer V3相似的训练时间”设置 \(L=3\)。

### 5. 实验数量与充分性
- **实验组数**：共7个环境 × 5种方法（None, SAC, TD3, DR3, MLE DR3），但None仅用于MLE/SLE测量，不参与奖励对比。每种方法独立训练3个随机种子。
- **评估规模**：每个种子80个episode（奖励），每个MLE测量20个初始状态。
- **消融实验**：附录B中对MLE计算参数（迭代次数、样本数）进行了消融，验证收敛性。
- **充分性评价**：实验覆盖了多种维度的环境、3种主流DRL算法、加入了噪声测试，且报告了置信区间，设计较为全面。但仅基于模拟环境，未在真实机器人上验证；仅测试了Dreamer V3的正则化效果，未尝试其他架构；训练时未加入噪声（只在测试时加），可能低估实际部署中的鲁棒性。

### 6. 论文的主要结论与发现
1. **DRL策略可诱发混沌**：所有复杂高维环境（Walker系列、Cheetah）中，SAC、TD3、Dreamer V3策略均产生正MLE和负SLE，表明状态轨迹混沌且对初始扰动敏感；简单环境中仅Dreamer V3产生轻微混沌。
2. **混沌导致奖励不稳定**：高维环境下的奖励MLE为正，说明微小扰动可导致总奖励显著变化，形成“分形回报曲面”。
3. **MLE正则化降低混沌**：加入正则化后，Dreamer V3的MLE下降（如Walker Stand从0.1688降至0.0654），同时平均奖励基本不变或略有提升（如Walker Run从646.3升至698.4）。
4. **鲁棒性增强**：在添加高斯观测噪声的测试中，MLE正则化在4/6个环境中显著提升了Dreamer V3的性能（Cartpole Balance, Cartpole Swingup, Walker Walk, Walker Run），其余2个环境（Walker Stand, Cheetah Run）持平。

### 7. 优点
- **创新性**：首次使用李雅普诺夫指数谱来**量化已训练DRL策略的混沌程度**，并以此指导正则化，为策略鲁棒性提供新视角。
- **方法简洁有效**：正则项仅依赖Dreamer V3已有的RSSM多轨迹预测，无需额外模型，易于集成。
- **实验系统全面**：对比多种基线方法，覆盖多个难度级别的环境，并评估了状态和奖励两个层面的稳定性。
- **评估客观**：报告了95%自助置信区间，并在附录中验证了MLE计算参数的收敛性，增加了结果的可信度。

### 8. 不足与局限
- **依赖模型精度**：MLE正则项的有效性依赖于RSSM对状态散度的准确估计，若环境动力学复杂难以建模，效果可能减弱。
- **未验证其他架构**：仅对Dreamer V3进行了正则化，未测试SAC/TD3上的适用性，通用性待验证。
- **部分环境效果有限**：在Walker Stand和Cheetah Run上性能与基线持平，可能因为正则化强度不足或环境本身对发散不敏感。
- **训练-测试分布差异**：训练时未引入噪声，仅在测试时添加，可能与实际部署中在线噪声环境不匹配。
- **计算开销**：虽然声称训练时间接近，但 \(L=3\) 的多轨迹预测仍会增加前向计算成本，大规模应用时需进一步权衡。
- **未考虑真实世界因素**：实验仅在模拟器中完成，未涉及传感器延迟、执行器误差、部分可观测性等现实挑战。

（完）
