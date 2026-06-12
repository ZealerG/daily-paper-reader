---
title: Continuous Strategy Adaptation and Discrete Switching Driven by Environment and Internal State in Meta-Learning
title_zh: 连续策略适应与环境及内部状态驱动的离散切换在元学习中
authors: "Chen, J., Taira, M., Doya, K."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.729424v1.full.pdf"
tags: ["query:graph-part"]
score: 6.0
evidence: 使用带时变元参数的强化学习模型分析行为
tldr: 本研究分析了小鼠在两步决策任务中的行为策略变化，结合四种分析方法揭示连续与离散策略切换机制。stay概率和GLMM分析表明学习进步促使向基于模型的价值学习策略转变，伴随选择坚持增强。元参数动态显示学习加快、模型策略参与增加、随机性升高。有限内部状态模型发现了最优价值学习态与次优自我重复态之间的离散切换。在奖励变化时，两种过程交互导致不完全适应。
source: biorxiv
selection_source: fresh_fetch
motivation: 理解元学习中策略如何根据环境和内部状态连续或离散地调整，现有研究分别关注连续或离散变化，缺乏统一分析。
method: 使用stay-switch概率、GLMM、时变元参数强化学习粒子滤波、有限内部状态模型四种方法分析小鼠行为。
result: 学习促使模型策略和坚持增加；不确定奖励引发探索；元参数动态反映连续适应；状态切换捕捉离散转变。
conclusion: 元学习同时包含连续参数调整和离散状态切换，在奖励变化时两者交互导致不完全适应。
---

## 摘要
行为策略可以根据环境和内部状态变化，逐渐或突然地改变，从而实现灵活适应。这种策略调节是元学习（学习如何学习）的核心。以往的研究使用假设连续或离散变化的模型和理论分析了时间或条件依赖的策略变化。在这里，我们使用四种不同方法分析小鼠在两步决策任务中的行为：留守-切换选择概率分析；给定前序任务事件下的选择和反应时间的广义线性混合模型；通过新颖的多步粒子滤波方法拟合具有时变元参数的强化学习模型；以及拟合一个有限内部状态模型，该模型根据离散状态转换产生选择和反应时间。总之，留守概率和广义线性混合模型分析揭示，学习进展促使向基于模型、基于价值的学习策略转变，伴随选择持久性增加。更不确定的奖励设置或其中的变化导致随机、探索性行为。元参数动态显示，随着学习进展，学习更快，基于模型的策略参与更多，选择随机性更高，选择持久性发展更快，但对最终决策的贡献较少。面对不确定奖励设置或其变化时的探索性行为由较慢的遗忘和更大的基于模型贡献支持。有限内部状态模型发现了一个试验级别的切换，在最优基于价值的学习状态和次优自我重复状态之间。元参数动态反映了连续策略变化，而状态转换捕捉了突然的离散策略切换。在中间时间尺度上，当奖励设置改变时，两个过程相互作用：小鼠持续处于自我重复状态，导致在不完全适应的情况下尝试基于模型的策略。

## Abstract
Behavioral strategies can change in response to environmental and internal states, either gradually or abruptly, enabling flexible adaptation. Such strategy regulation is central to meta-learning, the ability to learn to learn. Previous studies analyzed temporal or condition-dependent strategy change using models and theories that assume continuous or discrete changes. Here, we analyze the mice's behavior in a two-step decision task using four different approaches: stay-switch choice probability analysis; generalized linear mixed model (GLMM) of choice and reaction time (RT) given preceding task events; fitting a reinforcement learning (RL) model with time-varying meta-parameter by a novel multiple-step particle filtering method; and fitting a finite internal state (FIS) model that produces choice and RT depending on discrete state transition. Together, the stay probability and GLMM analyses reveal that learning progress encourages a shift toward a model-based, value-based learning strategy, accompanied by elevated choice perseveration. More uncertain reward settings or changes in them lead to random, exploratory behavior. Meta-parameter dynamics show faster learning, greater involvement of a model-based strategy, higher choice stochasticity, and more rapid development of choice perseveration with less contribution to the final decision as learning progresses. Exploratory behavior in the face of uncertain reward settings or changes in those settings is underpinned by slower forgetting and greater model-based contribution. FIS modeling discovered a trial-level switch between an optimal value-based learning state and a suboptimal self-repeating state. Meta-parameter dynamics reflect continuous strategy changes, while state transitions capture abrupt, discrete strategy switches. At an intermediate timescale, when reward settings change, two processes interact: mice persist in a self-repeating state, leading to attempts at model-based strategy with incomplete adaptation.