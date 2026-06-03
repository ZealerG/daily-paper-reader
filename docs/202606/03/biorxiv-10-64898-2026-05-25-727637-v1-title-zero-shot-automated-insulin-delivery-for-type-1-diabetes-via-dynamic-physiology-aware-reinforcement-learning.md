---
title: "Title: Zero-shot automated insulin delivery for type 1 diabetes via dynamic physiology-aware reinforcement learning"
title_zh: 通过动态生理感知强化学习实现1型糖尿病的零样本自动胰岛素输注
authors: "Yoo, J., Rachim, V. P., Lee, Y., Lee, J., Park, S.-M."
date: 2026-05-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.25.727637v1.full.pdf"
tags: ["query:graph-part"]
score: 7.0
evidence: 应用动态强化学习于自动胰岛素输送
tldr: 针对1型糖尿病胰岛素自动输注中依赖个性化参数、需碳水化合物宣告等问题，提出零样本动态生理感知强化学习控制器DPARC。它仅基于连续血糖监测和胰岛素输注历史，无需预先个性化设置即可在1小时内适应，在仿真和猪体实验中提升了血糖范围时间，达到接近个性化模型性能，且潜在表征与生理指标相关。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有自动胰岛素输注系统大多依赖固定个性化参数，难以适应快速生理变化，且需碳水化合物宣告，增加用户负担。
method: 提出DPARC，利用滚动24小时历史窗口，通过强化学习推断潜在生理动态，无需个性化参数或用户干预，实现零样本自适应控制。
result: 在仿真和猪体实验中，DPARC在1小时内适应，提升血糖范围时间，接近全个性化模型性能，且学到的表征与胰岛素敏感性等生理指标相关。
conclusion: DPARC作为零样本自动胰岛素输注的临床前概念验证，有望推动未来人体试验，减少用户负担。
---

## 摘要
1型糖尿病的胰岛素治疗需要根据血糖、进餐、生理状态和体力活动不断调整剂量。这种高要求的自我管理带来沉重负担并增加给药错误风险，因此亟需能够减少用户干预的自动胰岛素输注（AID）系统。然而，许多现有系统依赖固定的个体化参数，可能无法充分适应快速或未观察到的生理变化。我们开发了动态生理感知强化学习控制器（DPARC），这是一种零样本胰岛素优化器，无需预先个性化、碳水化合物声明或预设受试者特定参数，即可从近期连续血糖监测（CGM）和胰岛素输注历史中推断潜在生理动力学。DPARC使用滚动24小时CGM和胰岛素历史窗口，但闭环操作可在观察1小时数据后开始，通过用中性归一化填充初始化未观察历史并逐步替换为观测值。在计算机模拟中，单个冻结的DPARC策略在1小时内适应，与每日总胰岛素条件化强化学习基线相比提高了目标范围内时间，并在随机时间、碳水化合物量、吸收变异性和跳过进餐的随机未声明进餐下接近完全个性化模型的上限性能。在未声明进餐的监督猪实验中，DPARC无需手动配置即维持了高目标范围内时间，支持大型动物可行性，但需要前瞻性人体评估才能确定临床疗效。学习到的潜在表征与生理标志物（包括胰岛素敏感性和血浆胰岛素浓度）相关，支持生理对齐和解释锚点。总体而言，这些发现将DPARC作为临床前概念验证的零样本AID框架，为未来监督下的人体评估奠定基础。

## Abstract
Insulin therapy in type 1 diabetes requires constant dose adjustment based on blood glucose, meals, physiological states, and physical activity. This demanding self-management imposes a substantial burden and increases dosing-error risk, underscoring the need for automated insulin delivery (AID) systems that reduce user intervention. However, many current systems depend on fixed, individualized parameters and may not fully adapt to rapid or unobserved physiological changes. We developed the Dynamic Physiology-Aware Reinforcement learning Controller (DPARC), a zero-shot insulin optimizer that infers latent physiological dynamics from recent continuous glucose monitoring (CGM) and insulin-delivery history without prior personalization, carbohydrate announcements, or preset subject-specific parameters. DPARC uses a rolling 24-hour CGM and insulin-history window, but closed-loop operation can begin after 1 hour of observed data by initializing unobserved history with neutral normalized padding and progressively replacing it with observations. In silico, a single frozen DPARC policy adapted within 1 hour, improved time in range compared with a total daily insulin-conditioned reinforcement learning baseline, and approached the upper-bound performance of a fully personalized model under stochastic unannounced meals with randomized timing, carbohydrate amounts, absorption variability, and meal skipping. In supervised porcine studies under unannounced meals, DPARC maintained high time in range without manual configuration, supporting large-animal feasibility while prospective human evaluation is needed before clinical efficacy can be established. Learned latent representations correlated with physiological markers including insulin sensitivity and plasma insulin concentration, supporting physiological alignment and explanatory anchors. Collectively, these findings support DPARC as a preclinical proof-of-concept zero-shot AID framework for future supervised human evaluation.