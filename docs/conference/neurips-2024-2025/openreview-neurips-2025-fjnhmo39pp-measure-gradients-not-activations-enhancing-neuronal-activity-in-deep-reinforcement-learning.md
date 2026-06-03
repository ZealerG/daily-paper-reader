---
title: "Measure gradients, not activations! Enhancing neuronal activity in deep reinforcement learning"
title_zh: 测量梯度而非激活：增强深度强化学习中的神经元活动
authors: "Jiashun Liu, Zihao Wu, Johan Obando-Ceron, Pablo Samuel Castro, Aaron Courville, Ling Pan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FjNHmO39pp"
tags: ["query:graph-part"]
score: 9.0
evidence: 通过基于梯度的神经元活动改进深度RL训练
tldr: 本文指出深度强化学习代理存在神经元活动丢失问题，传统基于激活统计的休眠神经元比率在复杂架构中失效。作者提出以梯度统计代替激活统计来衡量神经元学习能力，并据此引入梯度引导的神经元增强方法。实验表明该方法在多种深度RL架构上显著提升了代理的持续学习能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 696, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1379, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1410, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1396, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 729, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 636, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 630, \"height\": 264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 800, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1305, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fjnhmo39pp/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1402, \"height\": 739, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1131, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 553, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1377, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 716, \"height\": 659, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1104, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 845, \"height\": 747, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 869, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fjnhmo39pp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1525, \"height\": 336, \"label\": \"Table\"}]"
motivation: 深度RL代理的神经元活动丢失损害持续学习，现有方法在复杂架构下统计能力不足。
method: 将统计目标从激活切换为梯度，用梯度范数指导神经元保护与激活。
result: 在多个深度RL基准上改善了代理的适应性和学习稳定性。
conclusion: 梯度导向的神经元活动增强是更有效的深度RL训练策略。
---

## Abstract
Deep reinforcement learning (RL) agents frequently suffer from neuronal activity loss, which impairs their ability to adapt to new data and learn continually. A common method to quantify and address this issue is the $\tau$-dormant neuron ratio, which uses activation statistics to measure the expressive ability of neurons. While effective for simple MLP-based agents, this approach loses statistical power in more complex architectures. To address this, we argue that in advanced RL agents, maintaining a neuron's **learning capacity**, its ability to adapt via gradient updates, is more critical than preserving its expressive ability. Based on this insight, we shift the statistical objective from activations to gradients, and introduce **GraMa** (**Gra**dient **Ma**gnitude Neural Activity Metric), a lightweight, architecture-agnostic metric for quantifying neuron-level learning capacity. We show that **GraMa** effectively reveals persistent neuron inactivity across diverse architectures, including residual networks, diffusion models, and agents with varied activation functions. Moreover, **re**setting neurons guided by **GraMa** (**ReGraMa**) consistently improves learning performance across multiple deep RL algorithms and benchmarks, such as MuJoCo and the DeepMind Control Suite. **We make our code available.**

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
- **研究动机**：深度强化学习代理在训练过程中常出现神经元活动丢失（neuronal activity loss），导致其难以适应新数据分布，损害持续学习能力。
- **已有方法的局限**：广泛使用的 τ-休眠神经元比率（ReDo）基于激活值统计来衡量神经元表达能力，在简单 MLP 架构中有效，但在现代复杂架构（如残差网络、扩散模型、多种激活函数）中统计能力显著下降。
- **核心观点**：在先进 RL 代理中，维持神经元的**学习能力**（通过梯度更新适应新分布的能力）比维持表达能力更为关键；激活值无法准确反映学习潜力，而梯度幅度能更好地衡量这一能力。

## 2. 方法论
- **核心思想**：将神经元健康评估的统计目标从激活值（activation）切换为梯度幅度（gradient magnitude），提出 **GraMa**（**Gra**dient **Ma**gnitude Neural Activity Metric）。
- **关键技术细节**：
  - 对于第 ℓ 层第 i 个神经元，定义其学习能力分数 \( G_{\ell}^i = \frac{\mathbb{E}_{x \sim D} |\nabla_{h_{\ell}^i} L(x)|}{\frac{1}{H_\ell} \sum_k \mathbb{E}_{x \sim D} |\nabla_{h_{\ell}^k} L(x)|} \)，其中 \( \nabla_{h_{\ell}^i} L(x) \) 是损失对该神经元输出的梯度幅度。
  - 设定阈值 τ，当 \( G_{\ell}^i \le \tau \) 时判定该神经元为低学习能力神经元。
  - 基于 GraMa 的神经元重置机制 **ReGraMa**：每间隔 Δt 步，检测所有神经元的学习能力分数，对低于阈值的神经元重新初始化（输入权重恢复至原始分布，输出权重置零）。
- **轻量性**：梯度信息在反向传播后已存在，无需像激活方法那样存储中间输出，计算和内存开销极低（论文 Fig. 5 左图展示了相比 ReDo 的执行时间优势）。
- **理论性质**：在传统 ReLU-MLP 架构中，证明若神经元休眠（s=0）则梯度也为零，即 GraMa 与 ReDo 在此类架构上等价。

## 3. 实验设计
- **使用的环境/场景**：
  - **MuJoCo**（Ant、Walker2d）
  - **DeepMind Control Suite**（Dog Walk、Dog Stand、Humanoid Walk、Humanoid Stand、Quadruped Run 等）
- **Benchmark 算法与架构**：
  - 残差网络策略：BRO-net（含 LayerNorm、残差连接）
  - 扩散模型策略：DACER（U-net + Swish 激活）
  - MLP 策略变体：使用 ReLU、Sigmoid、Tanh 激活函数的 SAC
- **对比方法**：
  - 主要对比：ReDo（基于激活的休眠神经元重置）
  - 额外对比：S&P（Shrink & Perturb）、ReBorn、CBP（Continual Backpropagation）
  - 消融实验：不同阈值 τ、网络缩放、与 L2 初始化/权重衰减的组合

## 4. 资源与算力
- 文中在 Fig. 5 左图提到执行时间对比基于 **RTX 3090 GPU**，但未明确说明实验所用的具体 GPU 数量、总训练时长或总计算预算。
- 附录提供了所有超参数，但未报告整体算力消耗。因此，资源算力细节**不完整**，无法精确量化。

## 5. 实验数量与充分性
- **实验数量**较多且系统：
  - 在 4 个 DMC 任务上对比 ReGraMa vs ReDo vs vanilla BRO-net（Fig. 8）
  - 在 2 个 MuJoCo 任务上对比 DACER 架构（Fig. 10）
  - 在 3 种激活函数（ReLU、Sigmoid、Tanh）的 SAC 上评估（Fig. 12）
  - 网络缩放实验（1×、2×、4× 网络深度）（Fig. 9）
  - 阈值鲁棒性分析（τ 在 [0, 0.1] 均匀采样）（Fig. 13，附录 B）
  - 消融实验：修剪神经元对性能的影响（Fig. 7）、与 L2 初始化/权重衰减的组合（附录 Table 9）
  - 额外对比：在 BRO-net 上与其他塑性维护方法（S&P、ReBorn、CBP）比较（Table 8）
- **充分性分析**：
  - 每种条件采用 **3-4 个随机种子**，报告均值和误差棒（标准差或区间），统计可靠。
  - 覆盖了多种主流架构（残差、扩散、MLP 变体）和基线方法，实验设计**客观公平**。
  - 作者还提供了理论证明（定理 1）补充实验证据。
- **总体评价**：实验充分，考虑到了架构多样性、关键超参数敏感性、消融分析，结论可信。

## 6. 主要结论与发现
1. **激活指标在复杂架构中失效**：ReDo 在 BRO-net 等复杂网络中错误地重置了学习能力高的神经元，同时遗漏了真正低学习能力的神经元（Fig. 3）。
2. **梯度指标 GraMa 更准确**：GraMa 能有效识别长期低学习能力的神经元，且该状态不可逆（Fig. 6）；基于 GraMa 修剪神经元对性能影响最小（Fig. 7）。
3. **ReGraMa 显著提升性能**：在残差网络、扩散模型、多激活函数架构下，ReGraMa 均比 ReDo 和 vanilla 基线获得更高回报，并保持更低的低能力神经元比例（Fig. 8, 10, 12）。
4. **鲁棒性好**：对阈值 τ 不敏感（Fig. 13），在网络缩放时也能稳定提升性能（Fig. 9）。
5. **与正则化方法兼容**：ReGraMa 可与 L2 初始化或权重衰减结合进一步提升效果（Table 9）。

## 7. 优点
- **新颖性**：首次将梯度幅度作为神经元学习能力的度量标准，从根本上解决了激活指标在复杂架构下的统计偏差问题，视角新颖。
- **简洁高效**：GraMa 计算轻量（利用已有梯度信息），架构无关，易于嵌入现有 RL 训练流程。
- **实验系统全面**：覆盖多种主流架构、多种环境、多种对比方法，并包含丰富的消融和鲁棒性分析，结论坚实。
- **理论支撑**：给出了与传统方法等价的定理证明，增强了方法的可信度。
- **开放代码**：提供了可复现的开源代码，有利于后续研究。

## 8. 不足与局限
- **计算资源未充分报告**：未明确说明实验所用的具体 GPU 数量、总训练时长，影响精确复现和成本评估。
- **架构覆盖有限**：作者自述仅评估了三种代表性架构（残差、扩散、MLP 变体），未涉及大规模 Transformer 策略或多任务环境，泛化性仍需扩展。
- **阈值设定仍需经验**：虽然论文表明对阈值不敏感，但在不同任务间仍需要大致选择，未提供自适应阈值方案。
- **部分现象未完全解释**：例如 Tanh 激活下 GraMa 比例虽优但仍逐渐上升（Fig. 12c），作者仅归因于激活函数或重置机制的相互作用，尚待进一步分析。
- **未讨论在离散动作或 image-based RL 上的全面评估**：仅涉及连续控制，视觉强化学习中的适应情况未深入验证。

（完）
