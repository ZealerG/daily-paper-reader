---
title: Multi-turn Reinforcement Learning with Preference Human Feedback
title_zh: 基于偏好人类反馈的多轮强化学习
authors: "Lior Shani, Aviv Rosenberg, Asaf Cassel, Oran Lang, Daniele Calandriello, Avital Zipori, Hila Noga, Orgad Keller, Bilal Piot, Idan Szpektor, Avinatan Hassidim, Yossi Matias, Remi Munos"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=rVSc3HIZS4"
tags: ["query:graph-part"]
score: 4.0
evidence: 多轮强化学习算法，基于偏好反馈
tldr: 提出基于镜像下降的多轮偏好强化学习算法，在表格设置中证明收敛性。该方法拓展了RLHF到多轮对话场景，但与图划分无直接关联。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-rvsc3hizs4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 1124, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-rvsc3hizs4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rvsc3hizs4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 484, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rvsc3hizs4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rvsc3hizs4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1766, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-rvsc3hizs4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1581, \"height\": 562, \"label\": \"Table\"}]"
motivation: 现有RLHF仅模拟单步偏好，无法处理需要长期规划的多轮交互。
method: 提出多轮偏好强化学习的镜像下降策略优化算法。
result: 证明了算法收敛性，并在多轮任务中取得良好效果。
conclusion: 该工作推动了RLHF在多轮场景下的应用。
---

## Abstract
Reinforcement Learning from Human Feedback (RLHF) has become the standard approach for aligning Large Language Models (LLMs) with human preferences, allowing LLMs to demonstrate remarkable abilities in various tasks.  Existing methods work by emulating the human preference at the single decision (turn) level, limiting their capabilities in settings that require planning or multi-turn interactions to achieve a long-term goal. In this paper, we address this issue by developing novel methods for Reinforcement Learning (RL) from preference feedback between two full multi-turn conversations.  In the tabular setting, we present a novel mirror-descent-based policy optimization algorithm for the general multi-turn preference-based RL problem, and prove its convergence to Nash equilibrium.  To evaluate performance, we create a new environment, Education Dialogue, where a teacher agent  guides  a  student  in  learning  a  random  topic,  and  show  that  a  deep  RL variant of our algorithm outperforms RLHF baselines. Finally, we show that in an environment with explicit rewards, our algorithm recovers the same performance as a reward-based RL baseline, despite relying solely on a weaker preference signal.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：现有的 RLHF（基于人类反馈的强化学习）方法仅模拟单步（单轮）的偏好，即一次输入输出后立即给予反馈。这无法处理需要多步规划或长期目标的多轮对话、工具使用等场景。
- **意义**：多轮交互中，一个动作的优劣往往取决于后续行为，单步反馈难以反映长期影响。例如，销售员在初期要高价看似不利，但可能是提升最终成交价的策略。
- **目标**：将 RLHF 扩展到多轮对话的完整轨迹级别偏好反馈，设计能收敛到纳什均衡（即策略对任何对手策略都更优）的算法，并验证其在真实场景中的有效性。

### 2. 论文提出的方法论

- **核心思想**：将多轮交互建模为上下文马尔可夫决策过程（CMDP），偏好反馈给出在两个完整对话轨迹之间的比较。基于**镜像下降（Mirror Descent, MD）** 与**自对弈（Self-play）** 框架，定义新的**偏好 Q 函数**，使得全局优化可以转化为每个状态的局部优化。
- **技术细节**：
  - 定义正则化偏好模型 \( P_\alpha(\pi \succ \pi') = P(\pi \succ \pi') - \alpha \mathrm{KL}_p(\pi \|\mu) + \alpha \mathrm{KL}_p(\pi' \|\mu) \)，其中 \(\mu\) 为参考策略，\(\alpha\) 为 KL 正则化系数。
  - 定义偏好 Q 函数 \( Q^{\pi,\pi'}_\alpha(x_h, y_h) \)，表示从状态 \(x_h\) 采取动作 \(y_h\) 后，策略 \(\pi\)（从当前状态开始）与策略 \(\pi'\)（从初始状态开始）相比的期望正则化偏好。
  - **MTPO 更新规则**（以状态 \(x_h\) 为例）：
    \[
    \pi_{t+1}(\cdot|x_h) = \arg\max_\pi \eta_t \langle \pi, Q^{\pi_t,\pi_t}_\alpha \rangle[x_h] - \alpha\eta_t \mathrm{KL}(\pi\|\mu)[x_h] - (1-\alpha\eta_t) \mathrm{KL}(\pi\|\pi_t)[x_h]
    \]
    可显式写为：
    \[
    \pi_{t+1}(y_h|x_h) \propto \mu(y_h|x_h)^{\alpha\eta_t} \pi_t(y_h|x_h)^{1-\alpha\eta_t} e^{\eta_t Q^{\pi_t,\pi_t}_\alpha(x_h,y_h)}
    \]
  - **MTPO-τ** 变体：使用几何混合策略 \(\pi^{\alpha}_t\)（插值当前策略与参考策略）来增加探索，更新使用 \(Q^{\pi^\alpha_t,\pi^\alpha_t}_\alpha\)。
- **理论保证**：证明 MTPO 和 MTPO-τ 的 last-iterate 收敛到正则化偏好模型的纳什均衡，收敛率为 \(O(HQ^2/(\alpha^2 t))\)。同时提供多轮 RLHF 版本的收敛性。
- **深度学习实现**：采用 Actor-Critic 架构，用 GAE 估计优势，策略损失包含优势项和 KL 正则化，价值损失为 MSE。还使用批归一化等技术。

### 3. 实验设计

- **环境与数据集**：
  1. **Education Dialogue**：新构建的偏好环境，教师（agent）教导学生（环境）随机主题。使用 Gemini Ultra 生成完整对话和偏好标签，基于“宪法”原则定义良好教学。数据已开源。
  2. **Car Dealer**（来自 LMRL-Gym）：奖励环境，汽车销售员与顾客对话，目标最大化成交价。奖励通过提取成交价得到。偏好信号由 BT 模型从奖励采样。
- **基准模型**：
  - 监督微调（SFT）
  - 单轮奖励 RLHF（将每个对话轮次视为独立单步，用修改后的偏好提示训练）
  - 单轮值函数 RLHF（通过 Monte Carlo 估计值函数）
  - 单轮 Nash-MD（基于直接偏好的单轮算法）
  - 多轮 RLHF（使用 BT 模型学习奖励，再用标准 RL 优化）
  - MTPO 与 MTPO-τ（本文提出）
- **评估协议**：用 Flan-T5 XL 和 Gemini Ultra 作为评判模型进行侧边对比（side-by-side evaluation），计算偏好概率。

### 4. 资源与算力

- 论文明确说明使用 **4×4 Tensor Processing Units (TPUs)** 进行训练，每次训练步骤（step）耗时约 0.1 秒（学习一个 10 轮对话）。
- 未精确给出总 GPU/TPU 时数，也没有说明单次完整实验的耗时或使用的总机器数。但可以根据 50000 步骤估算大约 5000 秒（约 1.4 小时）每实验（单 TPU Pod 内 16 核并行），实际因多次运行和搜索超参数会更多。

### 5. 实验数量与充分性

- **实验数量**：
  - Education Dialogue 环境：使用 3 个不同随机种子运行每个方法，生成 1600 个对话样本进行 Flan-T5 XL 评估（表 1）；再用 1000 个样本做 Gemini Ultra 评估（表 2）。
  - Car Dealer 环境：使用 5 个种子报告均值和 95% 置信区间（表 3）。
  - 消融包括对比多轮 vs 单轮、MTPO vs MTPO-τ、RLHF vs 直接偏好优化。
- **充分性**：实验较充分，覆盖了有奖励和无奖励场景，对比了多种基准，且统计了标准差和置信区间。但仅在一个偏好环境（Education Dialogue）和一个奖励环境（Car Dealer）进行，缺少更多多样化对话任务（如客服、任务导向对话）。此外，评判模型为 LLM（Flan/ Gemini），可能引入偏差，但作者已确认 Flan-T5 XL 与 Gemini Ultra 相关。

### 6. 论文的主要结论与发现

- **多轮方法显著优于单轮方法**：使用完整轨迹级别偏好（MTPO、多轮 RLHF）在所有实验中大幅超过单轮基线，表明长期规划的有效性。
- **直接偏好方法（MTPO/MTPO-τ）优于多轮 RLHF**：在 Education Dialogue 中，MTPO 和 MTPO-τ 的偏好胜率高于基于 BT 奖励的 RLHF，证实了直接建模偏好的优势（更贴近真实人类反馈，不受奖励假设局限）。
- **MTPO-τ 略优于 MTPO**：添加混合策略增加了探索，避免了策略过早确定化导致的反馈信息不足。
- **在奖励环境 Car Dealer 中，MTPO 与直接用奖励信号的标准 RL 性能相当**，尽管仅使用偏好信号，证明了方法的通用性。

### 7. 优点

- **理论完备**：给出了多轮偏好 RL 中首个收敛到纳什均衡的算法证明。
- **统一框架**：将 RLHF、直接偏好优化、自对弈等思想整合到一个多轮框架中，且公式可推广至 token 级（见 Remark 3.3）。
- **实用性强**：即使忽略 MD 稳定性项，仅使用策略梯度和 KL 正则化仍取得优异效果，实现简单。
- **开源环境**：发布了 Education Dialogue 数据集，推动了多轮偏好学习的研究。
- **实验设计合理**：使用不同检测模型（Flan-T5 XL 和 Gemini Ultra）进行双重验证，控制了偏好来源偏差。

### 8. 不足与局限

- **实验规模有限**：仅使用 T5-Large（770M）和 T5-XL（3B）模型，未在更大规模 LLM（如 7B+）或主流模型（Llama、Gemini 等）上验证。
- **环境非真实人机交互**：所有对话和偏好均由 LLM 生成，可能不完全反映真实人类偏好和动态。虽然用 Gemini Ultra 进行对齐，但仍需人类评估验证。
- **计算资源描述不够详细**：未提供单次训练总耗时、能耗等信息，难以复现资源需求。
- **未对比其他多轮 RLHF 变体**（如基于 token 级别的 DPO 扩展），也未与更先进的在线偏好优化方法（如 APA、SPO）比较。
- **收敛率证明仅针对表格设定**，深度学习实现的稳定性主要靠 KL 正则化，缺少 MD 项的影响未实验分析。
- **Car Dealer 环境中，偏好信号来自 BT 模型，这与论文“脱离 BT 假设”的主张略有矛盾**，但作为奖励环境对照仍然有效。

（完）
