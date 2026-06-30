# 公文处理 Skills

一套面向中文公文生成、修改和审查的 AI Skills 包。

它不是范文堆砌，也不是简单提示词合集，而是把公文处理拆成一套可复用的工作系统：先判断文种和意图，再选择结构框架，最后用句式、成分、工作剧情和审查清单完成写作、改稿或把关。

## 适合谁用

- 需要快速起草工作简报、总结、通知、方案、讲话等材料的人。
- 手里有参考资料，但不知道如何组织成正式公文的人。
- 已经有一版粗稿，需要改得更正式、更有结构、更有高度的人。
- 需要审查公文是否能正式使用、是否存在硬伤的人。
- 想把“给一个主题就能引导完成公文”的流程交给 AI 执行的人。

## 它能解决什么问题

传统公文写作常见难点有三个：

1. **不知道写成什么文种**：同样一个主题，可能是简报、总结、通知、方案或讲话。
2. **不知道材料怎么展开**：只有几条事实，写出来容易空、散、像流水账。
3. **不知道怎么把关**：结构、标题、首段、数据、上级依据、语言风格都可能出问题。

这个 Skills 包把这些难点拆成了可执行规则：

- 用 `intake-and-routing.md` 判断意图和文种。
- 用 `document-frameworks.md` 选择对应公文框架。
- 用 `writing-foundations.md` 控制标题、首段和句式。
- 用 `work-plots-and-verbs.md` 从启动、执行、保障、反馈四阶段补足工作表达维度。
- 用 `components-and-logic.md` 处理成分、逻辑、高度、产品化和概念封装。
- 用 `review-checklist.md` 做正式使用前的审查把关。

## 核心能力

### 1. 生成公文

用户可以只给一个主题，也可以提供参考资料、会议记录、工作素材、上级文件摘录或粗略要求。

技能会完成：

- 判断文种。
- 选择框架。
- 组织材料。
- 生成标题、首段、主体和结尾。
- 对缺失事实使用 `[待补充]` 标记。

### 2. 修改公文

支持轻度润色、结构重写和完整重写。

可以处理：

- 标题不平行。
- 首段不够正式。
- 语言口语化。
- 结构像流水账。
- 工作缺少高度。
- 材料有事实但表达不成体系。

### 3. 审查公文

审查时先给结论：

- `通过`
- `基本通过`
- `不通过`

然后列出具体问题、原因和修改建议，重点检查：

- 文种是否匹配。
- 框架是否完整。
- 上级依据是否准确。
- 成绩是否有事实和数据支撑。
- 问题和整改是否对应。
- 语言是否符合公文场景。
- 是否存在正式使用风险。

## 支持文种

| 类别 | 文种 |
|---|---|
| 基础工作类 | 工作简报、工作计划、工作总结、工作报告、心得体会 |
| 部署行文类 | 工作通知、会议通知、印发通知、工作方案 |
| 讲话研究类 | 领导讲话、述职报告、调研报告、理论文章 |
| 宣传纪要类 | 新闻稿、通讯稿、先进事迹、会议纪要 |
| 党建专题类 | 民主生活会对照检查材料、党课、微型党课、演讲稿 |

## 低成本交互设计

这个技能的目标不是让用户填写复杂表单，而是尽量少问、尽快产出。

交互规则：

- 用户资料明确时，直接处理，不追问。
- 用户说“按我的参考资料写”“根据附件生成”“直接改这份稿子”时，直接产出。
- 信息不足但可以写初稿时，用 `[待补充]` 标记缺失内容。
- 只有文种、用途或关键事实不清会导致方向错误时，才提问。
- 最多 3 轮交互；每轮只问 1-3 个关键问题。
- 第 3 轮后必须进入产出，不继续追问。

三轮交互顺序：

1. **确认方向**：给谁看、用在什么场景、是否指定文种。
2. **补核心事实**：做了什么、有什么数据、是否有上级依据。
3. **确认输出**：篇幅、语气、是否需要问题和下一步。

## 安装方式

把 `skills/official-document-writing` 放到目标平台的 Skills 目录，或按目标平台的导入规则导入即可。

这个包不依赖外部接口、数据库或脚本。

```text
skills/
└── official-document-writing/
    ├── SKILL.md
    ├── agents/
    ├── references/
    └── assets/
```

## 使用示例

生成工作简报：

```text
使用 $official-document-writing，帮我写一份关于基层治理网格化管理的工作简报。
```

按参考资料生成：

```text
使用 $official-document-writing，请按照我提供的参考资料，写一份专项整治工作总结。
```

修改已有稿件：

```text
使用 $official-document-writing，把这份总结改得更正式、更有高度，但不要改动事实和数据。
```

审查正式通知：

```text
使用 $official-document-writing，审查这份通知是否能正式下发，指出硬伤并给修改建议。
```

只给主题时：

```text
使用 $official-document-writing，主题是“青年干部能力提升”，你判断适合写什么材料，并先给我一版初稿。
```

## 目录结构

```text
official-document-writing-skill-kit/
├── README.md
└── skills/
    └── official-document-writing/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        ├── references/
        │   ├── intake-and-routing.md
        │   ├── writing-foundations.md
        │   ├── work-plots-and-verbs.md
        │   ├── components-and-logic.md
        │   ├── document-frameworks.md
        │   ├── generate-workflow.md
        │   ├── revise-workflow.md
        │   └── review-checklist.md
        └── assets/
            └── templates/
                ├── 00-template-index.md
                ├── work-brief.md
                ├── annual-work-plan.md
                ├── work-summary.md
                ├── work-report.md
                ├── learning-reflection.md
                ├── notice-general.md
                ├── notice-meeting.md
                ├── notice-issuance.md
                ├── implementation-plan-complete.md
                ├── implementation-plan-direct.md
                ├── leader-speech-before.md
                ├── leader-speech-progress.md
                ├── duty-report.md
                ├── research-report-experience.md
                ├── research-report-problem.md
                ├── theory-article.md
                ├── news-meeting.md
                ├── news-activity.md
                ├── news-research.md
                ├── communication.md
                ├── advanced-deeds.md
                ├── democratic-life-check.md
                ├── party-lecture.md
                ├── micro-party-lecture-speech.md
                ├── meeting-minutes-itemized.md
                └── meeting-minutes-news-style.md
```

## 文件说明

### `SKILL.md`

技能主入口，负责：

- 识别生成、修改、审查三类任务。
- 控制低成本交互。
- 路由到对应 reference。
- 规定不可编造事实、不可乱改固定提法等底线。

### `references/`

| 文件 | 作用 |
|---|---|
| `intake-and-routing.md` | 意图判断、文种判断、三轮以内交互协议 |
| `writing-foundations.md` | 标题、句式、首段、公文化语言 |
| `work-plots-and-verbs.md` | 工作启动、执行、保障、反馈剧情和常用动词 |
| `components-and-logic.md` | 成分、水分干货、六大逻辑、地空对接、产品化、概念封装 |
| `document-frameworks.md` | 各文种框架 |
| `generate-workflow.md` | 生成流程 |
| `revise-workflow.md` | 修改流程 |
| `review-checklist.md` | 审查清单 |

### `assets/templates/`

提供 27 个结构模板，只写结构和占位，不虚构具体内容。

## 质量原则

- 不虚构上级文件、领导讲话、政策名称、时间、数字、荣誉和组织事实。
- 上级精神和固定提法必须原文使用。
- 单位既有格式优先于通用模板。
- 公文最终必须落到工作：措施、成绩、问题、计划、要求或责任。
- 缺少事实时用 `[待补充]` 或少量追问，不用漂亮话填空。
- 修改稿默认做最小必要修改，不做无关重写。
- 审查稿必须先给结论，再列问题。

## 设计边界

这个项目提供的是公文处理方法和结构化技能，不替代：

- 单位正式办文规范。
- 上级通知的具体要求。
- 对真实政策、会议、数据和事实的核验。
- 法定公文格式的最终人工把关。

## 来源说明

本包根据用户提供的公文写作方法材料进行结构化整理，重点提炼可执行流程、框架模板和检查标准。为便于分享和二次使用，内容采用方法论重述和模板化表达。

