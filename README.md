# Research Supervisor · 科研导师

一个以问题、证据和决策为核心的科研 skill，主要服务于 AI / 计算机实验研究。从选题与 idea 发现，推进到实验诊断、方法改进、数据集构建与论文论证。

## 站在巨人的肩膀上

**本项目以 [HKUSTDial / Supervisor-Skills](https://github.com/HKUSTDial/Supervisor-Skills) 为主要基础，整合其他优秀科研 skills 的工作方法，再围绕两条研究路线进行重写和调整。感谢上游作者与社区公开分享科研经验、方法和工具。**

我们把“站在巨人的肩膀上”写在这里，也把来源、修改和许可保留在项目中。这是一份有明确来源的整合与改编，不将上游贡献宣称为本项目原创。

| 致谢项目 | 作者 / 团队 | 本项目吸收的思路 |
| --- | --- | --- |
| **[Supervisor-Skills](https://github.com/HKUSTDial/Supervisor-Skills)**（主要基础） | Yuyu Luo（骆昱宇）与贡献者 | 导师式选题判断、研究价值与能力匹配、贡献类型、从证据组织论文、投稿前审查 |
| [Claude Scholar](https://github.com/Galaxy-Dawn/claude-scholar) | Gaorui Zhang 与贡献者 | 将研究问题、证据、主张边界与后续决策连接起来，保留研究过程中的约定与变化 |
| [Scientific Agent Skills](https://github.com/K-Dense-AI/scientific-agent-skills) | K-Dense AI / K-Dense Inc. 与贡献者 | 替代假设、可区分的预测、批判性思考，以及观察、解释和结论的区分 |
| [AI Research Skills](https://github.com/Orchestra-Research/AI-Research-SKILLs) | Orchestra Research 与贡献者 | 多种 idea 构思视角、实验与反思循环、失败经验和项目记忆 |

整理由 [Yang Tian（TyangJN）](https://github.com/TyangJN) 提出需求并与 Codex 共同完成。上游作者未参与审核，也未为本项目背书。

具体参考模块、审读版本和实质修改见 [来源说明](references/provenance.md)；许可与第三方通知见 [LICENSE](LICENSE)。

## 两条找 idea 与推进研究的路线

### 路线 A：从已有数据集发现问题，改进方法

```text
寻找 / 选择数据集，明确任务与使用场景
    ↓
寻找近邻工作与有代表性的方法，建立可信基线
    ↓
运行方法，检查重复出现的失败与适用边界
    ↓
提出解释和替代解释，用小实验区分它们
    ↓
针对证据支持的问题进行改进
    ↓
独立评估、消融或其他适当验证 → 形成论文论证
```

数据集是有效入口。关键在于把“找一个数据集跑模型”逐步变成“在什么条件下出现了什么问题，为什么发生，如何验证和解决”。一次跑分落后不自动否决想法，一次涨点也不自动证明机制。详见 [路线 A](references/dataset-first.md)。

### 路线 B：从新问题或评估缺口出发，验证数据集的必要性

```text
发现不足、新问题或现有评估遗漏
    ↓
检查最接近的已有数据集与评估能否回答问题
    ↓
构建少量初步数据与对照，验证标注和测量
    ↓
判断：缺口真实存在吗？新数据能增加什么认识或用途？
    ↓
必要性、测量可靠性与增量用途得到支持后，规划完整构建
    ↓
完整数据集、基线、分析与文档 → 形成论文论证
```

若证据不足，可以修订、缩小、复用已有数据或停止当前版本。模型低分本身不能证明新数据集有价值；模型排名没有变化，也不能单独否定它。详见 [路线 B](references/benchmark-first.md)。

两条路线可以切换：已有数据无法观察目标问题时，从 A 转入 B；初步数据暴露稳定失败机制时，从 B 转入 A。切换依据新增证据，并相应调整范围。

## 本整合版的主要调整

这些是面向本项目使用场景的设计选择，不代表所有上游项目都存在同一种问题。

| 关注点 | 本项目的处理 |
| --- | --- |
| 想法是否值得继续 | 根据价值、近邻工作、可检验性和真实资源作条件判断；不使用通用分数门槛或录用概率裁决 |
| 方法跑得不好 | 先检查实现、比较条件、测量和替代解释；依据可信证据决定继续、调整或停止 |
| 是否该扩大数据集 | 先验证必要性、有效性、可靠性和增量用途；规模由覆盖需求、精度与预算决定 |
| 实验是否足以支持结论 | 区分探索与确认，检查评估集复用、统计单位、不确定性与主张边界 |
| 尚未取得结果的写作 | 只写计划、假设或预期；不编造结果、数字、引用或“初步发现” |
| 写作形式 | 服务于论证，不固定段落数、贡献数、文献数或标点规则 |
| 持续推进 | 记录有信息量的失败与决策；实验循环有预算和停止条件 |
| 使用成本 | 按需读取参考文件，不要求另装上游 skills、MCP、知识库或脚本 |

## 安装与使用

这是一个基于 `SKILL.md` 的指令包，没有 Python / Node 运行依赖。模型的检索、文件读写和实验执行能力由使用它的 agent 环境提供。

### 在 Codex 中安装

将本仓库克隆到个人 skills 目录中。目标目录已经存在时，先检查其中的本地修改，避免覆盖。

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/TyangJN/research-supervisor.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/research-supervisor"
```

也可以下载仓库，将包含 `SKILL.md`、`references/`、`assets/`、`agents/` 和 `LICENSE` 的完整文件夹放入 skills 目录。安装后在 Codex 的技能列表中查找“科研导师”，或在对话中显式调用 `$research-supervisor`。

### 使用示例

**从数据集出发：**

```text
使用 $research-supervisor。我已经选了一个数据集，准备比较三个现有方法。
帮我检查任务、数据划分和基线是否合适，并设计发现问题的第一轮实验。
已有材料：[数据说明 / 代码 / 论文]
资源约束：[算力 / 时间 / 标注预算]
```

**准备构建新数据集：**

```text
使用 $research-supervisor。我发现现有评估可能遗漏了某种能力，想做新数据集。
请先检索最接近的已有资源，设计一个小规模试点，判断是否值得完整构建。
不要把模型低分直接当作必要性的证明。
```

**实验不理想时：**

```text
使用 $research-supervisor。方法平均指标没有提升，但部分场景有差异。
根据这些日志和结果，区分实现问题、比较不公平、统计波动和机制不成立，
提出下一步最能改变判断的实验。
```

不必先填满所有信息；skill 应从已有材料开始，只追问会改变下一步的缺失信息。一次性讨论直接回答，持续项目可使用 [研究记录模板](assets/research-record.md)。

## 文件结构

```text
research-supervisor/
├── SKILL.md                         # 主入口、阶段判断和共同原则
├── agents/openai.yaml               # Codex 展示信息与默认提示
├── assets/research-record.md        # 轻量研究记录模板
├── references/
│   ├── dataset-first.md            # 路线 A
│   ├── benchmark-first.md          # 路线 B
│   ├── evidence-and-experiments.md  # 证据、诊断与实验设计
│   ├── writing-and-review.md       # 论文论证与审查
│   └── provenance.md               # 来源、版本与修改记录
├── LICENSE
└── README.md
```

## 验证与适用边界

v1.0.0 已通过技能结构、相对链接和展示元数据检查，并用三个合成场景检查行为：方法无平均提升且反复使用测试集、用少量挑选难例提议扩建 benchmark，以及无实验结果时要求撰写论文摘要。

这些检查用于发现指令问题，没有实际运行科研实验，不能证明本 skill 提高研究质量、保证新颖性或提高论文录用率。它主要面向 AI / 计算机实验研究；理论、定性和其他研究范式需要采用相应证据标准。真实研究仍需依据原始文献、数据、实验及研究者判断。

欢迎用可公开的实际案例提出 issue：说明输入、预期行为、实际问题及改进建议，帮助继续修正研究判断与工作流程。

## 许可

本整合版采用 **[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)**，遵循主要来源 Supervisor-Skills 的仓库许可；第三方 MIT 通知一并保留。再分发和改编时，请保留来源与许可，并注明修改。完整说明见 [LICENSE](LICENSE) 和 [来源说明](references/provenance.md)。
