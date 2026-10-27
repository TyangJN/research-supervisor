# 来源、修改与许可

本版本由用户提出需求并与 Codex 共同整理，日期为 2026-10-27。以 Supervisor-Skills 为基础，结合下列项目的工作方法，重写为以用户两条研究路线为核心的 skill。不是上游官方版本，上游作者没有为本版本背书。

## 主要来源

- **HKUSTDial / Supervisor-Skills**，Yuyu Luo 与贡献者：[仓库](https://github.com/HKUSTDial/Supervisor-Skills)。审读时记录的提交 `a20d76ef3979b804d7dbf599d577826957e0a8a9`。参考 `idea-evaluator`、`benchmark-paper-template`、`intro-drafter`、`paper-writer`、`pre-submission-reviewer`、`deep-research`；保留问题价值、能力匹配、论文类型区别、贡献与证据对应。仓库 [LICENSE](https://github.com/HKUSTDial/Supervisor-Skills/blob/main/LICENSE) 为 CC BY-NC-SA 4.0；部分技能元数据为 CC BY 4.0，本整合版采用仓库层面的 CC BY-NC-SA 4.0。
- **Galaxy-Dawn / Claude Scholar**，Gaorui Zhang：[仓库](https://github.com/Galaxy-Dawn/claude-scholar)。审读时记录的提交 `d394fb599ed9e6ea2212a9e6daa864345fe97a26`。参考 `research-ideation/references/research-contract.md`、`results-analysis`、`paper-self-review`；吸收问题、证据、主张边界和持续决策的连接。MIT。
- **K-Dense AI / Scientific Agent Skills**，K-Dense Inc.：[仓库](https://github.com/K-Dense-AI/scientific-agent-skills)。参考 2026-10-27 审读的 `hypothesis-generation` v2.4、`scientific-critical-thinking` v1.5、`scientific-brainstorming` v1.4、`literature-review` v1.11；吸收替代假设、可区分预测与证据限制，未引入生物医药专属流程。所参考文件标注 MIT。
- **Orchestra Research / AI Research Skills**：[仓库](https://github.com/Orchestra-Research/AI-Research-SKILLs)。审读时记录的提交 `773a52944ba4747a18bd4ae9ade53fff041adcbc`。参考 `21-research-ideation/brainstorming-research-ideas` 与 `0-autoresearch-skill`；吸收构思视角、实验/反思双层循环、失败经验和项目记忆。MIT。

通知保存在 [LICENSE](../LICENSE)。链接用于署名和后续审读，不要求每次使用时联网加载上游。

## 实质修改

1. 以“现有数据集—方法—问题—改进”和“新问题—初步数据—必要性—完整构建”为入口，增加阶段判断和切换。
2. 将固定生命周期、GPU/工时门槛、五维分数裁决改为条件、证据和不确定性驱动的建议。
3. 将实验落后自动否决改为实现、测量、比较和机制诊断；允许可信反证导致停止，也允许可靠负结果构成贡献。
4. 无实测时只写计划/假设，不用“初步结果”掩盖缺口。
5. 删除固定段落数、文献数、贡献数和标点禁令。
6. 新数据集先验证必要性、测量有效性/可靠性、增量用途，不以低分或排名变化作为充分条件。
7. 有预算和停止条件，不默认永久运行、收费算力或对外发布。
8. 轻量本地记录，不依赖另装 skill、知识库、MCP 或上游脚本。

## 验证边界

结构检查和合成场景试用只能发现部分指令问题，不能证明科研判断正确、新颖或提高录用率。用实际项目的证据、结果和反馈继续迭代。
