---
title: "M³HF: Multi-agent Reinforcement Learning from Multi-phase Human Feedback of Mixed Quality"
title_zh: M3HF：多智能体强化学习从混合质量的多阶段人类反馈
authors: "Ziyan Wang, Zhicheng Zhang, Fei Fang, Yali Du"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=2Sl6Ex7Vmo"
tags: ["query:graph-part"]
score: 9.0
evidence: 多智能体强化学习框架，利用多阶段混合质量人类反馈
tldr: 本文提出M3HF框架，将多阶段混合质量人类反馈融入多智能体强化学习，通过大语言模型解析反馈并持续优化策略，解决了复杂协调环境中奖励函数设计难的问题。实验表明该方法能有效利用专家与非专家反馈，提升多智能体系统的对齐效果和性能，为实际部署提供了可行方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1699, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1710, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1727, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1057, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 667, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1697, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-2sl6ex7vmo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1620, \"height\": 904, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-2sl6ex7vmo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 888, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2sl6ex7vmo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 885, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2sl6ex7vmo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-2sl6ex7vmo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 884, \"height\": 492, \"label\": \"Table\"}]"
motivation: 多智能体强化学习中奖励函数设计困难，易导致次优或偏差行为。
method: 提出M3HF框架，整合不同层次人类反馈，利用LLM解析并更新策略。
result: 实验证明该方法能有效利用混合质量反馈，改善多智能体协调行为。
conclusion: 该工作为多智能体强化学习提供了一种实用的人类反馈集成方法。
---

## Abstract
Designing effective reward functions in multi-agent reinforcement learning (MARL) is a significant challenge, often leading to suboptimal or misaligned behaviors in complex, coordinated environments. We introduce Multi-agent Reinforcement Learning from Multi-phase Human Feedback of Mixed Quality ($\text{M}^3\text{HF}$), a novel framework that integrates multi-phase human feedback of mixed quality into the MARL training process. By involving humans with diverse expertise levels to provide iterative guidance, $\text{M}^3\text{HF}$ leverages both expert and non-expert feedback to continuously refine agents' policies. During training, we strategically pause agent learning for human evaluation, parse feedback using large language models to assign it appropriately and update reward functions through predefined templates and adaptive weights by using weight decay and performance-based adjustments. Our approach enables the integration of nuanced human insights across various levels of quality, enhancing the interpretability and robustness of multi-agent cooperation. Empirical results in challenging environments demonstrate that $\text{M}^3\text{HF}$ significantly outperforms state-of-the-art methods, effectively addressing the complexities of reward design in MARL and enabling broader human participation in the training process.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将根据您提供的论文内容，按照您的要求生成一份结构化、深入、客观的中文总结。

---

# 论文总结：M3HF：基于混合质量多阶段人类反馈的多智能体强化学习

## 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：在多智能体强化学习（MARL）中，设计有效的奖励函数是一项重大挑战。在复杂、需要高度协调的环境中，稀疏或难以学习的奖励函数常常导致智能体收敛缓慢或陷入次优策略，甚至产生与目标不符的行为（misaligned behaviors）。
*   **研究动机**：传统的依赖环境固有奖励或单一专家设计的奖励函数不足以应对MARL中的复杂性。人类反馈（Human Feedback）作为一种额外的指导信号，有潜力帮助智能体更有效地学习。然而，现有方法（如RLHF）多聚焦于单智能体或单轮反馈，且通常需要高质量的专家经验，限制了其在实际MARL系统中的应用。
*   **整体含义**：本文旨在解决如何高效且鲁棒地利用**不同质量**（专家与非专家）和**多轮、迭代式**的人类反馈来引导MARL智能体的学习过程，从而提升其在复杂任务中的协调能力和最终性能。

## 2. 论文提出的方法论

*   **核心思想**：提出一个名为 **M³HF (Multi-agent Reinforcement Learning from Multi-phase Human Feedback of Mixed Quality)** 的框架。该框架将多阶段、混合质量的人类反馈直接集成到MARL的训练流程中，通过迭代的方式持续优化智能体的策略。
*   **关键技术细节**：
    1.  **形式化模型 (MHF-MG)**：提出“多阶段人类反馈马尔可夫博弈（MHF-MG）”，扩展了标准马尔可夫博弈，引入了人类反馈消息集 \(U\) 和人类策略 \(\pi_h\)。训练过程分为多个“世代（generation）”，每个世代包含大量训练迭代，之后进行一轮人机交互。
    2.  **人机交互流程**：
        *   **评估与反馈生成**：在每个世代，暂停智能体训练，生成**评估轨迹（rollout videos）**。人类（其策略优于当前智能体）观察这些视频并提供自然语言反馈 \(u_k\)。
        *   **反馈解析**：使用**大型语言模型（LLM）**（如GPT-4o）解析人类反馈，将其拆分为针对特定智能体或所有智能体的结构化指令。
        *   **奖励函数更新**：LLM根据解析后的指令，从一组**预定义的奖励函数模板**（如基于距离、行动、状态、时间等）中选择并实例化新的奖励函数 \(R_{ik}(s,a)\)。这些新奖励函数被加入每个智能体独有的**奖励函数池 \(P_i\)**。
    3.  **自适应权重调整**：最终用于下一世代训练的奖励函数是池中所有奖励函数（包括原始环境奖励）的**加权和**。权重通过以下两个机制动态调整：
        *   **权重衰减**：新加入的奖励函数具有较高初始权重，旧函数的权重随时间指数衰减（\(w_{i,m} = w_{i,m} \cdot \alpha^{M-m}\)），以鼓励利用最新的反馈信号。
        *   **性能导向调整**：对比使用新奖励函数后的智能体在**原始奖励**上的表现。如果性能提升，则增加新奖励函数的权重；反之则降低其权重。这确保了框架对低质量反馈的鲁棒性。
*   **算法流程**（文字描述）：
    *   **初始化**：为每个智能体初始化一个仅包含原始奖励函数的奖励池 \(P_i\)。
    *   **循环世代 \(k=0\) 到 \(K-1\)**：
        *   **训练阶段**：智能体使用当前加权奖励函数 \(\hat{R}_{ik}\) 在多智能体环境中进行大量训练。
        *   **评估与交互**：当满足条件（如固定轮数或性能停滞）时，暂停训练，生成评估轨迹。人类提供反馈 \(u_k\)。
        *   **解析与生成**：LLM解析反馈 \(u_k\)，生成新的奖励函数 \(R_{i,new}\)，并加入 \(P_i\)。
        *   **权重更新**：对新奖励函数初始化权重，对旧函数应用衰减，并进行性能导向调整，最终形成新的加权奖励函数 \(\hat{R}_{i,k+1}\) 用于下个世代的训练。

## 3. 实验设计

*   **环境与场景**：
    *   **主要环境**：**Overcooked**（多人协作烹饪游戏）的变体，包含三种难度递增的厨房布局（图2a-c：Overcooked-A, B, C）和两种沙拉食谱（图2d-e：Lettuce-Tomato, Lettuce-Onion-Tomato）。 这是一个部分可观测的宏行动环境。
    *   **扩展环境**：**Google Research Football (GRF) 5v5**（图5），用于验证方法的可扩展性。
*   **基准方法 (Baselines)**：
    *   **MAPPO** (Yu et al., 2022)
    *   **IPPO** (De Witt et al., 2020)
    *   **Macro-Action-Based Baseline** (来自 Xiao et al., 2022，选用了其中表现最好的两个方法 Mac-IAICC 和 Mac-CAC 的平均性能)。
*   **对比与消融实验**：
    1.  **总体性能对比**：在6个不同难度（布局x食谱）的组合下，对比M3HF和所有基线算法的性能。
    2.  **混合质量反馈鲁棒性**：设计实验，在智能体表现不佳时仍给予误导性的“高质量”反馈（图4a, 4b），测试框架鲁棒性。
    3.  **VLMs作为反馈源的可行性**：探索使用视觉语言模型（VLM，如Gemini-1.5-Pro-002）替代人类提供反馈，并比较其效果。
    4.  **消融实验**：
        *   **反馈管道消融**：对比“原始未解析反馈”、“仅LLM解析”和“完整M3HF（解析+权重调整）”。
        *   **反馈时间跨度消融**：对比“单阶段反馈”和“多阶段反馈”。
        *   **与内在奖励法对比**：将M3HF与基于内在奖励的方法（IRAT）进行比较，设计了三种不同复杂度的内在奖励函数（rw1, rw2, rw3）。

## 4. 资源与算力

*   论文明确提到了其计算资源：
    *   **硬件**：一个异构计算集群，运行Ubuntu Linux。包含多款CPU（如Dual Intel Xeon E5-2650, E5-2680 v2, E5-2690 v3），共计180个CPU核心和500GB内存。
    *   **GPU**：使用了3块 **NVIDIA A30** GPU 进行加速计算。
    *   **模型**：所有涉及语言驱动的反馈解析任务均使用 OpenAI 的 **GPT-4o-2024-11-20** 模型。VLM实验使用了 **Gemini-1.5-Pro-002**。
    *   论文未明确给出单次实验或整体实验的具体训练时长。

## 5. 实验数量与充分性

*   **实验数量**：实验设计较为全面。包含：
    *   6个主场景的完整性能对比。
    *   3类消融实验（管道、时间跨度、与内在奖励法对比）。
    *   1个混合质量反馈的鲁棒性测试。
    *   1个VLM可行性探索。
    *   1个在GRF环境下的扩展验证。
    *   所有主实验均报告了3个随机种子的结果，并展示了标准差。
*   **充分性与客观性**：
    *   **充分**：实验设计覆盖了框架的主要方面：整体性能、鲁棒性、不同组件的重要性、与传统方法的对比。消融实验设计清晰，有效验证了各模块的有效性。
    *   **客观/公平**：
        *   在Overcooked环境中，对比了多个SOTA基线（MAPPO, IPPO, Mac-based baseline）。
        *   对基线模型进行了超参数调优以确保公平比较。
        *   与IRAT等方法的对比也合理。
        *   需要注意的是，论文中的人类反馈来源明确，但“混合质量”实验中的“低质量反馈”是由作者模拟的，这虽然合理，但可能无法完全模拟真实世界中人类反馈的多样性和复杂性。

## 6. 论文的主要结论与发现

1.  **M3HF显著优于现有SOTA方法**：在几乎所有Overcooked场景和食谱组合中，M3HF都获得了比MAPPO、IPPO等基线方法更高的平均回报，学习速度更快，收敛性能更佳。
2.  **对低质量反馈具有鲁棒性**：实验证明，即使向智能体提供“低质量”或“具有误导性”的反馈，M3HF通过其自适应权重调整机制，性能也仅收到轻微影响（略低于IPPO基线但未显著退化），验证了其鲁棒性。
3.  **结构化解析与动态权重调整至关重要**：消融实验表明，完整的M3HF（包含LLM解析和权重调整）显著优于仅使用LLM解析或不解析的简化版本，证明了每个模块的必要性。
4.  **多阶段反馈优于单阶段反馈**：实验证明了迭代式、多阶段的人类反馈显著优于仅在训练开始时提供一次单阶段反馈，这为智能体策略的不断细化提供了可能。
5.  **VLM作为替代方案的初步探索**：当前的VLM在提供可操作性反馈方面能力有限，给出的反馈较为模糊（如“改善协调”），难以直接转化为有效的奖励函数，实际效果不佳。但这为未来更强大的多模态模型的应用提供了方向。

## 7. 优点

*   **方法创新性**：首次将**混合质量、多阶段**的人类反馈系统地融入MARL在线训练流程，提升了方法的实用性和可及性。
*   **算法严谨性**：提供了**理论分析**（Proposition 4.1和4.2），证明了对策略性能的估计是可靠的，并形式化地证明了算法对低质量反馈的鲁棒性。
*   **系统设计完整性**：提出的框架是一个完整的闭环系统，从反馈获取、LLM解析、奖励生成到权重调整环环相扣，设计精巧。使用LLM作为“翻译器”连接人类意图和可计算的奖励函数是一个亮点。
*   **实证说服力强**：在多个复杂度的场景和多样的基线方法上进行了广泛实验，并辅以全面的消融研究，实验设计和结果报告规范。
*   **推广潜力**：提出的MHF-MG框架可作为后续研究的新形式化基础。

## 8. 不足与局限

*   **人类反馈成本**：虽然论文提及旨在减少人类交互（最多5轮），但在真实部署中，每一轮都需要人类观看评估视频并提供文本反馈，这仍然是一个**显著的劳动密集型成本**，限制了系统的完全自动化。
*   **VLM局限性**：实验揭示了当前VLM在提供可操作、具体反馈上的不足，依赖更高级的LLM（如GPT-4o）进行解析是当前的瓶颈。如何更好地利用各类模型是未来发展需要解决的问题。
*   **实验环境局限性**：实验主要集中在Overcooked这个特定领域。虽然在GRF上进行了扩展，但论文也承认后续工作是必要的。结论的泛化能力到一个完全不同的领域（如自主驾驶、机器人操作）还有待验证。
*   **反馈偏差风险**：论文未深入探讨“混合质量”中可能存在的**系统性偏见**（如人类总是倾向于某种次优策略）。如果人类反馈存在一致性偏差，框架的鲁棒性机制可能无法完全消除这种影响。
*   **超参数敏感性**：权重衰减因子 \(\alpha\) 和调整系数 \(\beta\) 的设置对框架性能有影响，论文未对该超参数的敏感性进行深入分析或讨论其选择标准。

（完）
