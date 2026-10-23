---
layout: section
class: text-center
background: '#1e5f3a'
---

# 第2天
## 设计作品

智能软件工程

设计作品原型

确定技术选型

---

#  第2天工作任务

1. **用户故事清单 (docs/requirements/user_stories.md)**：
   * 至少编写 5 个符合 INVEST 规范的用户故事。
   * 每个故事需配有详细的 验收条件 (Acceptance Criteria)。

2. **原型展示（docs/software/prototype）**：提交利用 AI 生成的交互式原型页面。

3. **技术方案调研报告 (docs/software/architecture.md)**：
   * 论证核心技术选型。
   * 列出团队在未来 2 周内需要学习的新技术（制定自学计划与 Milestone）。


---

# 第2天第1部分智能软件工程

- 什么是智能软件工程 (Smart Software Engineering / AI4SE)？
- 智能软件工程的实践
- 大语言模型 (LLM) 在需求、代码生成与重构中的应用

---

# 第2天第1部分智能软件工程学习目标

- 理解 AI 对软件工程全生命周期的渗透：哪些环节被"加速"，哪些被"重塑"
- 区分 **AI 辅助开发** 与 **AI 原生软件** 两个不同命题
- 掌握目前主流的 AI 编码工具及其能力边界
- 认知 AI 带来的新问题：代码安全、版权、幻觉、对工程师能力的影响
- 能够评估：目前要从事的项目中，AI 可以应用到哪些环节
  
---

# 智能软件工程 (Smart Software Engineering)
### 当软件工程遇到大语言模型 (AI4SE)
学术界与工业界正经历从传统的“人写代码”向“人机协同 (Human-in-the-loop AI Coding)”的范式转变。
```mermaid
flowchart LR
    Idea[需求设想] -->|自然语言提示词
Natural Language Prompt| LLM[LLM / Agent]
    LLM -->|代码生成
Code Generation| Dev[人工审查、重构与微调]
    Dev -->|自动化测试
Automated Test Suite| QA[智能测试用例生成]
    QA -->|持续交付
Continuous Delivery| Deploy[自动部署与监控]
    Deploy -. 反馈 .-> Idea

    classDef input fill:#fff1d6,stroke:#c77b00,stroke-width:2px;
    classDef ai fill:#e8ddff,stroke:#714bc4,stroke-width:2px;
    classDef human fill:#dff5e5,stroke:#3c8c55,stroke-width:2px;
    classDef delivery fill:#dcecff,stroke:#3c6ea8,stroke-width:2px;

    class Idea input;
    class LLM ai;
    class Dev,QA human;
    class Deploy delivery;
```
* **研究热点**：基于 Agent 的软件工程自治、静态代码分析大模型、代码大模型对齐（RLHF for coding）。
* **核心生产力**：不仅是 Copilot 自动补全，更是在架构生成、单元测试生成方面的突破。


---
layout: two-cols
---
# AI 辅助开发（AI for SE）
把 AI 当工具，**提升软件工程的效率**

- AI 写代码、生成测试、修 Bug
- AI 读文档、做评审
- 工程师仍是主体

::right::

# AI 原生软件（SE for AI）
把 AI **嵌入软件本身**，成为产品能力

- 智能推荐、对话式交互
- 代码里跑着大模型
- 工程问题转为"如何可靠地使用AI"


💡 对具体项目：既在用 AI 辅助开发（已用AI工具做原型），又在考虑把 AI 算法模型作为作品功能——这正是两者的结合


---

# AI 在软件全生命周期中的应用

```mermaid{scale:0.6}
flowchart LR
    A[需求分析] -->|AI 辅助| A1[需求澄清
用户故事生成]
    B[系统设计] -->|AI 辅助| B1[架构建议
接口设计]
    C[编码实现] -->|AI 辅助| C1[代码补全
自动生成]
    D[系统测试] -->|AI 辅助| D1[测试用例生成
缺陷预测]
    E[系统维护] -->|AI 辅助| E1[缺陷定位
重构建议]

    A1 --> F[效率提升与质量改进]
    B1 --> F
    C1 --> F
    D1 --> F
    E1 --> F

    classDef phase fill:#eef5ff,stroke:#3973b9,stroke-width:1px;
    classDef capability fill:#e9f8ee,stroke:#3f9560,stroke-width:1px;
    classDef result fill:#fff1d8,stroke:#ca8016,stroke-width:2px;

    class A,B,C,D,E phase;
    class A1,B1,C1,D1,E1 capability;
    class F result;
```

---

# 国际主流 AI 编码工具一览

| 工具 | 定位 | 典型能力 |
|---|---|---|
| **GitHub Copilot** | 行内补全 | 内联代码补全、聊天交互、Copilot Workspace |
| **Cursor** | AI 优先编辑器 | 全库理解、AI 编辑、代码库问答 |
| **Claude Code** | 编程代理 | 多文件修改、任务拆解、自主执行 |
| **Codeium / Windsurf** | 替代方案 | 免费补全、多语言 |
| **JetBrains AI** | IDE 集成 | 在 IntelliJ/PyCharm 内使用 |
| **ChatGPT / Claude** | 通用对话 | 代码解释、面试题、文档生成 |
| **GitHub Copilot / CodeRabbit** | 代码评审 | 自动 PR 审查、找 Bug |

---
class: text-sm
---

# 中文主流 AI 编码工具一览

> 根据公共信息核实　时间：2026-10-14

| 工具（最新名称） | 定位 | 典型能力 |
|---|---|---|
| **Qoder CN（原通义灵码）**&#8203; | 阿里云 AI 编程智能体系列 | 补全 + Ask/Edit/Agent 三模式；Quest 2.0 规划、Subagent、MCP；多模型切换 |
| **CodeGeeX（智谱 Z.ai）**&#8203; | 开源代码大模型 + IDE 插件 | CodeGeeX4-ALL-9B（128K、支持 Function Call）；多语言补全、代码库问答；可内网私有化 |
| **文心快码（Baidu Comate）**&#8203; | 插件 + AI IDE（已并入「百度搭子」） | 超级补全、多智能体协同、SPEC 规范驱动；Figma 转前端代码；知识增强 RAG |
| **DeepSeek-V4（Pro / Flash）**&#8203; | 开源旗舰大模型（编程底座） | 1M 上下文；V4-Pro 为开源最佳 Agentic Coding；V4-Flash 快而省；开放权重可自部署 |
| **TRAE（原 MarsCode，字节跳动）**&#8203; | AI Development 平台（IDE / 插件 / CLI） | Agent 与 IDE 模式无缝切换；SOLO 端到端开发、设计稿转代码、多模态编程 |


---
class: text-sm
---

# 中文主流 AI 编码工具一览（续）
> 根据公共信息核实　时间：2026-10-14

| 工具（最新名称） | 定位 | 典型能力 |
|---|---|---|
| **CodeFuse（蚂蚁集团）**&#8203; | 企业级代码大模型 + 开源生态 | 补全 / 解释 / 单测 / 优化补丁；CodeFuse-Query 静态分析；金融级安全沙箱与脱敏 |
| **CodeBuddy（腾讯云代码助手）**&#8203; | 插件 + IDE + CLI 三端全覆盖 | 补全、单测、评审；Craft/Agent 智能体、MCP、Figma2Code、一键部署；混元 + DeepSeek 双轮 |
| **iFlyCode（科大讯飞）**&#8203; | 智能编程助手（SaaS / 私有化） | 生成、续写、纠错、解释、单测、调试、SQL、代码评审；70+ 语言、信创适配 |
| **Kimi Code（月之暗面）**&#8203; | 开源模型 + 编程工具（终端 / IDE） | K2.6 开源，可连续编码 13 小时、Agent Swarm 并行；截图 / 录屏生成前端代码 |
| **华为 CodeArts Snap** | 信创 / 鸿蒙 AI 编程助手（盘古） | 生成、问答、单测、解释、调试等八大场景；ArkTS/鸿蒙原生适配；纯离线内网 |


---
class: text-sm
---

# 中文主流 AI 编码工具补充说明
> 根据公共信息核实　时间：2026-10-14

**格局：由「三类」演化为「三层」**
- ① **一体化 Agent / AI IDE 平台**（主战场）：CodeBuddy、TRAE、Qoder CN、文心快码、CodeArts Snap
- ② **IDE 插件 / 行内补全**（类 Copilot）：iFlyCode、CodeFuse、CodeGeeX
- ③ **开源模型底座**（可自部署 / API）：DeepSeek-V4、GLM-5、Kimi K2.6、CodeGeeX4

**2026 三条主线**
- **Agent 化**：补全 → 多文件改写 → 全流程自主执行（Plan / Subagent / Skills / MCP·ACP 成标配）
- **平台收编**：文心快码→百度搭子、TRAE→豆包、通义灵码→Qoder CN、CodeBuddy 与 WorkBuddy 同账号同积分
- **开源追平闭源**：DeepSeek-V4-Pro 开源 Agentic Coding 最佳、GLM-5 SWE-bench Verified 77.8%、Kimi K2.6 比肩 GPT-5.4 / Opus 4.6

**三个记忆点**
- **CodeBuddy**：国产少见的**插件 / IDE / CLI 三端全覆盖**，已演进为「设计→编码→后端→部署」全流程 Agent 平台；与 WorkBuddy 同账号同积分（CodeBuddy 编码、WorkBuddy 办公）
- **CodeFuse**：偏企业级与金融，重代码知识库检索、静态分析与私有化，亦为开源主力贡献者
- **本土差异**：中文注释 / 需求转代码体验更佳 + 信创适配、等保三级、国密加密、私有化 / 纯离线内网

---
layout: two-cols
---

# ✅ AI 擅长

- 生成**样板代码**（CRUD、配置、DTO）
- 补全重复性高、有明确模式的内容
- 单测生成、注释生成、文档翻译
- 给出**常见问题**的已知解法
- 快速搭出一个可运行的原型


::right::


# ❌ AI 的局限

- **不理解业务语义**——它不知道"为什么这样设计"
- 生成看似正确实则**隐藏 Bug** 的代码
- **幻觉**：编造不存在的 API、库、函数
- 不会主动质疑不合理的需求
- 处理**大型复杂系统**的全局一致性能力有限
- 无法替你拍板架构决策


---
class: text-sm
---

# 幻觉（Hallucination）案例：AI 编造不存在的 API


```java
// AI 生成的代码（示例）
// 假设用了一个不存在的库方法
import com.example.redis.StringRedisTemplate;

public class CacheService {
    public String get(String key) {
        return redisTemplate
            .getOrElse(key, () -> "default"); // ❌ 该方法不存在
    }
}
```

AI 很自信地编造了一个 `getOrElse` 方法，看起来像通用的 Redis 缓存 API，但实际不存在。

```java
// ✅ 真实存在的 Redis API
public String get(String key) {
    String v = redisTemplate.opsForValue().get(key);
    if (v == null) {
        return "default";
    }
    return v;
}
```

⚠️ 结论：AI 生成代码必须经过**编译/运行验证**，以及**人工代码审查**，不能盲信。呼应第9周"代码质量工具"。


---

# AI 时代的安全新问题
- **Prompt Injection（提示注入）**：恶意用户通过输入让 AI 模型执行非预期指令
- **数据泄露**：把公司敏感代码喂给外部 AI，可能被用于训练
- **供应链风险**：AI 推荐的不熟悉依赖包可能存在恶意代码
- **不可审计性**：AI 生成的复杂代码，人类难以审查其正确性
- **版权模糊**：AI 生成代码是否存在版权问题，法律尚未统一

🔒 **应对**：企业会部署私有化模型 / 使用"带安全审查的AI" / 设置代码上传白名单 / 对AI生成的代码必须强制走评审流程

---
layout: two-cols
---

# AI 对软件工程师角色的冲击
- **初级编码工作被替代**：样板代码、重复工作交给 AI
- **工程师能力重心上移**：从"会写代码"转向"会提问、会审查、会架构"
- **Prompt Engineering** 成为软技能
- **更强调**：系统设计、领域理解、质量意识、责任心

::right::

# 启示

在项目里：

- 哪些工作 AI 能做（让 AI 做）
- 哪些工作只能人来判断（业务决策、架构取舍）
- 如何在作品中体现"人机协作"而非"AI 替代人"

---
layout: two-cols
---

# 第2天第2部分设计作品原型：理论


- 如何编写符合 INVEST 原则的用户故事 (User Stories)
- **实践指南**：利用 AI 辅助设计构建高保真原型

::right::

# 第2天第2部分设计作品原型：实践

- 编写用户故事
- 使用 AI 工具及原型设计工具设计软件作品原型（包括用户体验UX）


📋 检查：确认软件作品原型设计(docs/software/prototype)


---
class: text-sm
---

# AI 辅助原型设计：从自然语言到交互式代码
### AI-Assisted Prototyping

在进行大规模开发前，利用 AI 生成工具快速完成**高保真交互原型 (Interactive Prototype)**，能够极大降低需求偏离的风险。

* **工具推荐**：
  * **v0.dev / Bolt.new** (前端 UI 的自然语言生成)
  * **Figma AI** (组件化交互设计)
  * **Uizard** (手绘草图转换为高保真 UI)


给 AI 的 Prompt 示例：

"Generate a responsive Tailwind React dashboard for a Scientific Simulation Control System. It should contain an interactive 3D canvas placeholder (using Three.js icons), a left sidebar showing the simulation parameters (density, gravity, step size), a bottom panel showing a live-updated charting log for error rates, and a clear run/pause control cluster."为一个科学仿真控制系统生成一个响应式的 Tailwind React 仪表盘。该仪表盘应包含一个交互式 3D 画布占位符（使用 Three.js 图标）、一个显示仿真参数（密度、重力、步长）的左侧边栏、一个显示实时更新的误差率图表日志的底部面板，以及一个清晰的运行/暂停控制组件。

---
class: text-sm
---

# AI 辅助原型设计：从自然语言到交互式代码
### AI-Assisted Prototyping（中文工具版）
> 大规模开发前，用 AI 快速产出**高保真交互原型**，把需求偏离的风险提前暴露

**工具推荐**
- **一体化 AI 设计平台（国产主力）**：腾讯 **Ardot**、**MasterGo AI**（蓝湖）、**摹客 3 / 小摹 AI**、**即时设计 · 即时 AI**、**Pixso AI**
- **需求 / 原型驱动（偏产品经理）**：**墨刀 AI Agent 2.0**（PRD 文档 → 可点击原型）、**UXbot**（流程画布 + 一次生成整套应用）
- **设计稿转代码（D2C / MCP）**：**Ardot MCP**（直连 WorkBuddy / CodeBuddy / Cursor 一键还原代码）、**GemDesign MCP**、**Pixso 研发模式**（HTML / 鸿蒙 ArkUI / SwiftUI / Flutter）
- **海外对照（需稳定国际网络）**：v0.dev、Bolt.new、Figma Make、Uizard
- **注意**：**Motiff 妙多**已于 2026-07-31 停服，历史文件需在 2026-11-01 前导出

**给 AI 的 Prompt 示例（中文，可直接粘贴）**

> 为「汉语学习 Agent（AI 中文助教）」生成一个响应式的 React 学习工作台：左侧为学习档案侧边栏（HSK 等级、已学词量、待复习队列），中间为对话练习区（汉字＋拼音标注＋声调提示，含"跟读"语音按钮与实时发音评分），底部为实时更新的纠错日志面板（语法纠错、发音评分、生词自动入卡），右上角为"开始 / 暂停对话"控制组，并可一键切换「拼音 / 汉字 / 英译」显示层级。使用 Ant Design 组件规范、清新国风配色、4px 圆角，并导出可编辑设计稿 + React 代码。

---
class: text-sm
---

# 中文 AI 原型工具：三条路线，怎么选？

| 你的身份 / 目标 | 首选 | 理由 |
|---|---|---|
| **产品经理**：需求未定稿，先要能评审的东西 | 墨刀 AI Agent、摹客 3 / 小摹 AI | 中文需求理解好，PRD → 可点击原型，公测期免费 |
| **设计师**：要能继续精修的专业稿 | Ardot、MasterGo AI、Pixso AI | 可编辑矢量稿 + 组件库/设计系统 + 团队协作 |
| **开发者**：要能跑起来的前端代码 | Ardot MCP、GemDesign MCP、Pixso D2C | MCP 直连 IDE，按项目技术栈生成 React / Vue 代码 |
| **企业 / 涉密项目**：数据不能出厂 | Pixso 私有化、MasterGo 企业版、CodeArts 生态 | 支持私有化 / 纯离线内网、权限与审计 |

- **总结**：**生成能力看国产（中文语境 + 本土组件库），代码质量看 MCP 打通程度，长期可用性看平台合规与私有化能力。**
- **共同注意点**：AI 出的是「草稿级资产」——生成后必须走查边框场景、自适应与异常状态，业务规则仍由人拍板。

---

# 以汉语学习 Agent 为例理解用户体验设计

## 什么是用户体验设计？

**用户体验设计（UX Design）**：以用户为中心，让产品有用、易用，并带来良好的使用感受。

以“帮助初学者练习汉语的教育 Agent”为例：

- **有用**：围绕点餐、问路等真实场景，提升中文交流能力
- **易用**：支持文字或语音交流，按需提供拼音和翻译
- **友好**：使用适合学生水平的表达，纠错时给予鼓励
- **可控**：学生可以调整难度、请求提示或随时结束练习

**UX 不只是界面好看，更关注学生能否轻松开始、持续练习、真正学会。**

---

# 如何设计汉语学习 Agent 的体验？

1. **了解用户**：汉语水平如何？学习目标是什么？有哪些困难？
2. **明确任务**：例如“能用汉语点一杯饮料”，而不是笼统地“提高汉语”
3. **设计流程**：选择场景 → 示范表达 → 对话练习 → 反馈与复习
4. **提供帮助**：听不懂时可重复、放慢语速或显示拼音
5. **建立信任**：语音识别不确定时先确认；录音与保存前说明用途并征求同意

**设计重点：减少操作负担，让学生把注意力放在学习上。**

---

# 示例：练习用汉语点餐
## 点餐对话

Agent：“你好！你想喝什么？”

学生：“我想一个茶。”

Agent：“我明白了！点饮料时可以说：‘我想要一杯茶。’你试着说一次？”

学生：“我想要一杯茶。”

Agent：“很好！你想喝热茶还是冰茶？”

## 如何验证体验是否有效？

- **学习效果**：能否不看提示，独立完成类似对话？
- **使用体验**：是否容易找到提示、理解反馈？
- **学习感受**：是否敢于开口，愿意继续练习？

**根据学生的表现与反馈持续改进，而不只关注聊天时长。**

---

# 第2天第2部分设计作品原型实践：用户故事地图与技术方案调研
### Practice: User Story Mapping & Tech Stack Investigation
本周各组要将前期的软件定义转化为具体的研发路线，并完成原型设计。


* **检查点**：教师将评估**原型的可行性**。


---

# MVP：最小可用产品

**用最少的功能，让用户完成核心任务，并验证产品是否有价值。**

以 Helpdesk AI 为例：

- 用户提问，AI 回答常见问题
- 无法解决时，用户可以创建工单
- 用户评分，团队收集反馈

**先验证“能否解决问题”，再增加投诉分级、数据看板等功能。**

---
layout: two-cols
---
# 编写高质量的用户故事
### Writing INVEST User Stories
用户故事是敏捷开发中描述功能需求的核心工具。
**标准模板：**
> 作为一名 `[角色]`，
> 我想要 `[某种功能]`，
> 以便能够 `[实现某种价值]`。

#### INVEST 原则：
* **I**ndependent（独立的）
* **N**egotiable（可协商的）
* **V**aluable（有价值的）
* **E**stimable（可估算的）
* **S**mall（小巧的）
* **T**estable（可测试的）
::right::

#### 用户故事与验收标准实例：

```yaml
用户故事:
  角色: 作为一名结构工程师
  功能: 我想要一键导入 STEP 格式的文件
  价值: 从而避免手动转换格式造成的精度损失。

验收标准 (Acceptance Criteria - Gherkin 语法):
  场景: 导入一个有效的 STEP 模型
    Given 用户在主界面并点击了"导入"按钮
    When 用户选择了一个标准的 50MB "engine.step" 文件
    Then 系统应在 5.0 秒内完成解析并无损渲染
    And 系统状态栏应显示 "导入成功，包含 1420 个面"
```

参考案例：[客服智能体用户故事与验收标准](https://github.com/bettermorn/AIAgent/blob/main/docs/CSAgent_UserStory_AcceptanceCriteria.md)


---

# 案例：一个云服务平台用户故事地图

按业务流程（横轴）与商业价值分批（纵轴）绘制。

![用户故事地图](https://raw.githubusercontent.com/bettermorn/IntelligentSWEPractice/main/courseware/pages/imgs/UserStoryMap.png)



---
layout: two-cols
---

# 案例：客服智能体用户故事地图

::left::

```mermaid{scale:0.35}
flowchart TB

classDef epic fill:#CECBF6,stroke:#534AB7,color:#26215C,font-weight:bold;
classDef mvp fill:#9FE1CB,stroke:#0F6E56,color:#04342C;
classDef r2 fill:#B5D4F4,stroke:#185FA5,color:#042C53;
classDef r3 fill:#F5C4B3,stroke:#993C1D,color:#4A1B0C;

subgraph Backbone["业务流程（用户旅程主干）"]
    direction LR
    E1(["① 发起会话"]):::epic
    --> E2(["② 提出诉求"]):::epic
    --> E3(["③ 获得响应"]):::epic
    --> E4(["④ 工单跟踪"]):::epic
    --> E5(["⑤ 反馈评价"]):::epic
end

subgraph R1["Release 1 · 核心闭环（必须价值）"]
    direction LR
    S1_1["创建会话<br/>填写 session_id / user_id"]:::mvp
    S2_1["描述问题<br/>自动识别意图"]:::mvp
    S3_1["知识库命中<br/>返回带引用的答案"]:::mvp
    S4_1["自动创建工单<br/>返回工单号 / 状态"]:::mvp
    S5_1["星级评分 + 评论<br/>提交反馈"]:::mvp
end

subgraph R2plus["Release 2 · 体验与覆盖面（重要价值）"]
    direction LR
    S2_2["多轮记忆<br/>无需重复背景信息"]:::r2
    S3_2["知识库未命中<br/>降级提示并转人工"]:::r2
    S3_3["识别投诉情绪<br/>安抚式回应"]:::r2
    S4_2["同会话补充信息<br/>更新已有工单"]:::r2
end

subgraph R3plus["Release 3 · 效率与易用性（增值）"]
    direction LR
    S1_2["快捷问题<br/>一键发起提问"]:::r3
    S5_2["响应式布局<br/>移动端随时评价"]:::r3
end

E1 --> S1_1
E2 --> S2_1
E3 --> S3_1
E4 --> S4_1
E5 --> S5_1

S2_1 --> S2_2
S3_1 --> S3_2 --> S3_3
S4_1 --> S4_2
S1_1 --> S1_2
S5_1 --> S5_2
```

::right::


## 说明

- **业务流程主干**：发起会话 → 提出诉求 → 获得响应 → 工单跟踪 → 反馈评价，对应 README 中 `/chat`、`/feedback` 接口及会话管理能力。
- **Release 1（核心闭环，必须价值）**：创建会话、意图识别、知识库命中答案、自动建单、提交评分，构成最小可用闭环。
- **Release 2（体验与覆盖面，重要价值）**：多轮记忆、知识库未命中降级、投诉情绪识别、工单追加更新。
- **Release 3（效率与易用性，增值）**：快捷提问、移动端响应式布局。
  



---
layout: two-cols
---

# 第2天第3部分技术设计：理论
- 领域驱动设计方法 Domain-Driven Design (DDD)
- AI Agent,参考 [AI Agent参考资源](https://github.com/bettermorn/AIAgent/) 自行研究

::right::

# 第2天第3部分技术设计：实践

- 参考[技术参考](https://github.com/bettermorn/IntelligentSWEPractice/wiki/%E6%8A%80%E6%9C%AF%E5%8F%82%E8%80%83), 确认技术方案（语言、平台、框架、架构图；数据分析技术、人工智能算法模型、区块链、虚拟现实技术等）
- 规划新技术学习

📋 检查：确认技术设计方案

---

# 第2天第3部分技术设计学习目标
- 理解 AI 工程
- AI Agent技术选型需要思考的问题
- 理解如何设计AI Agent
- 理解为什么需要 DDD —— 解决"业务与代码脱节"问题
- 掌握**战略设计**：限界上下文、通用语言、上下文映射
- 掌握**战术设计**：实体、值对象、聚合、领域服务、仓储
- 能够为自己的项目画出限界上下文图
- 能够将一个业务场景转化为领域模型代码

---
class: text-sm
---

# AI 工程比较

|比较维度 |提示词工程|上下文工程|驾驭层工程|循环工程|
|---|---|---|---|---|
|核心问题|如何把任务表达清楚|模型当前需要知道什么|如何约束模型执行|如何通过多轮反馈完成任务|
|主要对象|指令、角色、示例、输出格式|文档、历史、状态、记忆、工具结果|运行时、工具、权限、沙箱、验证器|计划、行动、观察、反馈、重试、终止|
|关注粒度|单次调用或单条消息|当前调用所需的信息集合|一次受控任务运行|从开始到结束的完整任务轨迹|
|技术本质|语言控制和任务表达|信息选择、压缩、排序和注入|运行控制、权限约束和系统编排|反馈控制、状态转移和搜索优化|
|核心目标|提高单轮回答质量|提高信息相关性和完整性|提高安全性、稳定性和可观测性|提高复杂任务的完成率和可恢复性|

---
class: text-sm
---

# AI 工程比较（续）

|维度|提示词工程|上下文工程|驾驭层工程|循环工程|
|--|--|--|--|--|
|操作对象|单次调用的文本|上下文窗口里的全部内容|模型之外的运行时骨架|控制流与时间结构|
|时间尺度|一轮|一次会话|一个任务期（含多次工具调用）|跨多轮/多任务|
|交付物|一段字符串|一个上下文组装流水线|一套代码、接口、沙箱、权限|一张状态机/流程图|
|核心约束|指令是否被理解|注意力是稀缺资源|动作空间是否可观测、可回滚|过程是否收敛、何时停止|
|典型手段|角色设定、格式约束、示例、思维链|检索、记忆、摘要压缩、按需加载、子代理隔离|工具 schema、沙箱、状态持久化、错误回传格式、日志回放|终止条件、预算、计划-执行-验证、并行/串行、人工升级点|
|度量|指令遵循率、格式正确率|同模型下的任务成功率、token 成本|任务成功率、故障恢复率、安全事件|收敛率、步数/成本分布、人工介入率|



---

# AI Agent架构

```mermaid
flowchart TB
    A["用户或外部系统"]
    B["交互层/API"]
    C["Agent 编排器"]

    D["大语言模型"]
    E["工具调用层"]
    F["RAG 知识库"]
    G["短期与长期记忆"]
    H["结果验证与人工确认"]

    I["数据库"]
    J["业务 API"]
    K["搜索与文件处理"]
    L["日志、评估与监控"]

    A --> B
    B --> C
    C --> D
    C --> E
    C --> F
    C --> G
    C --> H
    E --> I
    E --> J
    F --> K
    H --> L

    classDef box fill:#ffffff,stroke:#1a1a1a,stroke-width:1.5px,color:#111111,font-size:15px
    class A,B,C,D,E,F,G,H,I,J,K,L box
    linkStyle default stroke:#1a1a1a,stroke-width:1.5px
```

参考[AI Agent常见工作流模式](https://github.com/bettermorn/AIAgent/blob/main/docs/AIAgentConcept.md#%E5%B8%B8%E8%A7%81agent%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%A8%A1%E5%BC%8F)


---
class: text-sm
---

# AI Agent类型

| 类型 | 工作方式 | 适用场景 | 主要特点 |
|---|---|---|---|
| 被动响应型 Agent | 接收用户明确指令后执行单次任务，不主动规划，也不会持续跟踪任务状态 | 问答、信息检索、文本生成、简单数据查询、客服 FAQ | 自主程度最低；响应速度快；行为可控；通常不具备长期记忆和连续执行能力 |
| 辅助决策型 Agent（Copilot） | 在用户主导下提供建议、草稿、分析结果或操作辅助，由用户确认后完成最终决策和执行 | 编程辅助、文档撰写、销售支持、数据分析、办公自动化 | 人机协作；用户拥有最终控制权；能够理解上下文并提供个性化建议；适合高风险或需要人工审核的任务 |
| 任务执行型 Agent | 用户给出目标后，Agent 会自行拆解任务、调用工具并执行多个步骤，但通常需要关键节点确认 | 自动生成报表、数据清洗、部署应用、处理工单、执行标准业务流程 | 具备一定规划和工具调用能力；可连续执行任务；在关键操作前通常需要人工审批；兼顾效率与可控性 |
| 半自主型 Agent | 仅需接收较高层次的目标，能够自主规划、执行、监控和调整任务，遇到异常或高风险情况时请求人工介入 | 复杂数据工程、自动化运维、研究分析、供应链管理、营销活动编排 | 自主程度较高；具备状态跟踪、错误恢复和动态调整能力；采用“人在回路中”机制；适合流程较复杂但仍需监督的任务 |
| 全自主型 Agent | 根据目标或约束条件独立完成任务，包括规划、决策、工具调用、执行、评估和迭代，通常无需人工逐步干预 | 长时间运行的监控系统、自动化交易模拟、虚拟企业运营、复杂科研探索、无人化流程 | 自主程度最高；能够持续运行和自我调整；对环境感知、记忆、规划和安全控制要求高；存在误操作、目标偏离和合规风险 |
| 多 Agent 协作系统 | 多个具有不同职责的 Agent 分工协作，由协调 Agent 或通信机制分配任务、汇总结果和处理冲突 | 软件研发团队模拟、复杂研究项目、端到端业务流程、跨部门自动化 | 通过角色分工提升复杂任务处理能力；可并行执行；系统设计和协作成本较高；需要统一权限、通信和结果校验机制 |

**高风险操作均采用“人在回路中”机制，Agent 可以生成建议、编排任务和提交申请，但涉及控制、工单关闭、成绩发布、科研任务提交等操作必须经过授权审批。**


---

# AI Agent 技术栈

|层级|主要职责|推荐技术|
|---|---|---|
|前端交互层|对话、文件上传、结果展示|React、Next.js、Vue、Nuxt|
|API 层|鉴权、限流、接口管理|FastAPI、NestJS、Spring Boot、Kong|
|Agent 层|Prompt、工具调用、状态和流程编排|LangGraph、LangChain、LlamaIndex|
|模型层|模型调用、路由和成本控制|OpenAI、Claude、Gemini、LiteLLM|
|数据层|业务数据、向量数据、缓存|PostgreSQL、pgvector、Redis、Milvus|
|基础设施层|部署、监控、日志和安全|Docker、Kubernetes、Prometheus、Vault|


更多内容，可参考 [AI Agent](https://github.com/bettermorn/AIAgent/blob/main/docs/)



---
layout: two-cols
class: text-sm
---

# 应用软件与 AI Agent：区别与联系

::left::

```mermaid
flowchart LR
    U[用户目标] --> A[AI Agent]
    A --> P[理解需求]
    A --> L[动态规划]
    A --> T[调用工具]
    T --> S1[数据库]
    T --> S2[Web应用/API]
    T --> S3[工作流/RPA]
    S1 & S2 & S3 --> R[执行结果]
    R --> A
    A --> O[反馈结果或完成任务]

    classDef agent fill:#dbeafe,stroke:#2563eb,stroke-width:2px;
    classDef app fill:#dcfce7,stroke:#16a34a;
    class A agent;
    class S1,S2,S3 app;
```

**核心关系：**

- 应用软件强调“提供什么业务功能”
- AI Agent强调“能否围绕目标自主理解、规划和行动”
- AI Agent通常调用应用软件、数据库和API完成任务
- 一个应用软件可以内置Agent；一个Agent也可以操作多个应用软件

::right::

| 对比维度 | 传统应用软件 | AI Agent |
|---|---|---|
| 核心定位 | 提供固定业务功能 | 面向目标自主完成任务 |
| 交互方式 | 菜单、按钮、表单、固定参数 | 自然语言、文档、语音、事件 |
| 执行逻辑 | 预先设计好的规则和流程 | 动态理解、规划、执行和调整 |
| 自主性 | 通常需要用户逐步操作 | 可自主选择步骤和调用工具 |
| 任务范围 | 单一、明确、流程固定 | 多步骤、开放、跨系统 |
| 结果特点 | 稳定、确定、易复现 | 灵活，但可能存在不确定性 |
| 典型例子 | ERP、OA、电商、银行系统 | 客服Agent、研究Agent、办公Agent |


应用软件是“可使用的业务工具”，  AI Agent是“能够理解目标并协调多个工具完成任务的智能执行层”。参考[AI Agent](https://github.com/bettermorn/AIAgent/)

---

# AI Agent技术选型需要思考的问题1-2

## 1. 编排框架（Orchestration Framework）
- 为什么选用 LangGraph，而不是 LangChain Agent / CrewAI / AutoGen？
- 是否需要支持多 Agent 协作？单 Agent 场景是否也需要图式编排？
- 是否需要显式的状态机（State Machine）来管理复杂的多步骤任务？
- 框架是否支持人工介入（Human-in-the-loop）和中断恢复（Checkpoint/Resume）？
- 框架的可观测性（Tracing/Debug）能力如何，是否便于排查问题？

## 2. 大模型选型（LLM Provider）
- 为什么选用 Claude / GPT / 国产模型（如Qwen千问、DeepSeek）？
- 是否需要支持多模型切换（Model Router）以平衡成本与效果？
- 模型的上下文窗口长度是否满足业务需求？
- 是否需要本地部署/私有化模型以满足数据合规要求？
- 模型的 Function Calling / Tool Use 能力是否成熟稳定？
---

# AI Agent技术选型需要思考的问题3-4

## 3. 记忆与上下文管理（Memory）
- 短期记忆（对话上下文）与长期记忆（用户画像、历史知识）如何分离存储？
- 为什么选用向量数据库（如 Milvus / Pinecone / Weaviate）而不是传统 KV 存储？
- 是否需要摘要压缩（Summarization）来控制上下文长度？
- 记忆的更新/遗忘机制如何设计（防止信息过期或污染）？

## 4. 工具调用与集成（Tool / Function Calling）
- 工具接口是否遵循统一的 Schema 标准（如 OpenAPI / MCP）？
- 为什么选用 MCP（Model Context Protocol）而不是自定义工具协议？
- 工具调用失败时的重试与降级策略是什么？
- 是否需要工具调用的权限隔离与审计日志？
  
---

# AI Agent技术选型需要思考的问题5-6
## 5. 检索增强（RAG）
- 为什么选用某种向量检索方案而不是纯关键词检索（BM25）？
- 是否需要混合检索（Hybrid Search：向量 + 关键词）？
- 文档切分（Chunking）策略如何选择（固定长度 vs 语义切分）？
- 检索结果的重排序（Rerank）是否必要？

## 6. 部署与运行时（Deployment / Runtime）
- Agent 是同步阻塞执行还是异步/流式（Streaming）执行？
- 是否需要容器化部署（Docker/K8s）以支持弹性扩缩容？
- 单实例 vs 多实例并发下，Agent 的状态如何持久化共享？
- 是否需要本地沙箱（Sandbox）隔离代码执行类工具的风险？

---

# AI Agent技术选型需要思考的问题7-8
## 7. 成本与性能（Cost / Performance）
- 预估的 Token 消耗量和调用频次是多少？是否在预算范围内？
- 是否需要缓存（Prompt Caching / 结果缓存）来降低成本？
- 延迟要求（P95/P99）是多少，所选方案能否满足？

## 8. 安全与合规（Security / Compliance）
- Agent 是否有权限访问敏感数据/执行高风险操作？如何做权限边界控制？
- 是否需要输出内容审核（Content Moderation）？
- 用户数据是否需要本地化存储以满足合规要求？

---
layout: two-cols
---

# 为什么需要 DDD？

传统开发的问题：

- 业务专家说的话，程序员翻译成代码后**语义走样**
- 一个 `User` 类被塞进了下单、支付、物流所有逻辑 → **贫血模型 / 上帝类**
- 团队越大，模块边界越模糊，"改一处，坏三处"


::right::

```java
// ❌ 贫血模型（Anemic Model）反例
public class Order {
    private String id;
    private BigDecimal amount;
    private String status;
    // 只有 getter/setter，没有行为
}

public class OrderService {
    public void pay(Order order) {
        // 所有业务逻辑都堆在 Service 里
        if (order.getStatus().equals("PAID")) {
            throw new RuntimeException("已支付");
        }
        order.setStatus("PAID");
        // ... 100 行判断逻辑
    }
}
```


⚠️ 领域知识散落在 Service 各处，无法复用、难以测试

---

# DDD 核心概念地图

```mermaid
graph TD
    A[战略设计 Strategic Design] --> A1[通用语言 Ubiquitous Language]
    A --> A2[限界上下文 Bounded Context]
    A --> A3[上下文映射 Context Mapping]
    B[战术设计 Tactical Design] --> B1[实体 Entity]
    B --> B2[值对象 Value Object]
    B --> B3[聚合 Aggregate / 聚合根]
    B --> B4[领域服务 Domain Service]
    B --> B5[仓储 Repository]
    B --> B6[领域事件 Domain Event]
```

---
layout: two-cols
---

# 1. 通用语言（Ubiquitous Language）

**做法**：业务专家 + 开发人员用**同一套词汇**，写进代码、文档、注释里，杜绝"翻译损耗"

**案例场景**：图书馆借阅系统

| 业务语言 | 代码命名 |
|---|---|
| 读者 | `Reader` |
| 借阅 | `Loan`（不是 `Borrow`）|
| 逾期 | `Overdue` |
| 续借 | `Renew` |

::right::

# 参考代码

```java
// ✅ 代码直接使用业务语言，无需注释解释
public class Loan {
    private Reader reader;
    private Book book;
    private LocalDate dueDate;

    public boolean isOverdue() {
        return LocalDate.now().isAfter(dueDate);
    }

    public void renew() {
        if (isOverdue()) {
            throw new CannotRenewException("逾期不可续借");
        }
        this.dueDate = dueDate.plusDays(14);
    }
}
```


💡 课堂练习：为你们的项目列出 10 个核心业务术语，中英文对照，作为团队"词汇表"


---

# 2. 限界上下文（Bounded Context）

一个大系统按业务边界拆分成多个"上下文"，**同一个词在不同上下文里可以有不同含义**

销售上下文

Product = 带价格、促销信息的商品


仓储上下文

Product = 带库存数量、货架位置的物品



物流上下文

Product = 带重量、体积、包装方式的货物






⚠️ **常见错误**：新手总想设计一个"万能 Product 类"给所有模块共用 —— 这正是 DDD 要避免的



---
layout: two-cols
---

# 3. 上下文映射（Context Mapping）

上下文之间如何协作？常见模式：



- **共享内核**（Shared Kernel）：两个团队共用一部分模型
- **防腐层**（Anti-Corruption Layer, ACL）：隔离外部/遗留系统的模型污染
- **发布者-订阅者**：通过领域事件解耦



::right::

```java
// 防腐层示例：隔离第三方支付接口的模型
public class PaymentAntiCorruptionLayer {

    private final ThirdPartyPaySDK sdk;

    public PaymentResult pay(Order order) {
        // 把第三方 SDK 的丑陋结构
        // 翻译成我们自己的领域模型
        ThirdPartyPayRequest req =
            new ThirdPartyPayRequest(
                order.getId().toString(),
                order.getAmount().toPlainString()
            );
        ThirdPartyPayResponse resp = sdk.charge(req);

        return resp.getCode() == 0
            ? PaymentResult.success()
            : PaymentResult.failed(resp.getMsg());
    }
}
```

---
layout: two-cols
---

# 4 实体 Entity
- 有唯一标识（ID）
- 有生命周期，属性可变
- 两个实体即使属性相同，ID 不同也不相等

```java
public class Reader {
    private final ReaderId id; // 标识
    private String name;
    private String phone;

    // equals 基于 id 判断
    @Override
    public boolean equals(Object o) {
        return o instanceof Reader r
            && id.equals(r.id);
    }
}
```
::right::

# 值对象 Value Object
- 没有标识，只有属性
- **不可变**（Immutable）
- 属性相同即相等

```java
public final class Money {
    private final BigDecimal amount;
    private final String currency;

    public Money(BigDecimal amount, String currency) {
        this.amount = amount;
        this.currency = currency;
    }

    public Money add(Money other) {
        // 不可变：返回新对象，不修改自身
        return new Money(
            this.amount.add(other.amount), currency);
    }

    @Override
    public boolean equals(Object o) {
        return o instanceof Money m
            && amount.equals(m.amount)
            && currency.equals(m.currency);
    }
}
```




---
layout: two-cols
---

# 5. 聚合与聚合根（Aggregate Root）

**聚合** = 一组相关对象的集合，对外只暴露**聚合根**，保证一致性边界


```java{scale:0.6}
// Order 是聚合根，OrderItem 是内部实体
public class Order {
    private OrderId id;
    private List items = new ArrayList<>();
    private OrderStatus status;

    // 外部不能直接操作 items 列表
    // 必须通过聚合根的方法
    public void addItem(Product product, int qty) {
        if (status != OrderStatus.DRAFT) {
            throw new IllegalStateException(
                "订单已提交，不能修改");
        }
        items.add(new OrderItem(product, qty));
    }

    public Money totalAmount() {
        return items.stream()
            .map(OrderItem::subtotal)
            .reduce(Money.ZERO, Money::add);
    }

    public void submit() {
        if (items.isEmpty()) {
            throw new IllegalStateException("订单为空");
        }
        this.status = OrderStatus.SUBMITTED;
    }
}
```

::right::


# 设计原则

- 一个事务只修改**一个聚合**
- 聚合内部保证不变量（invariant）：
  比如"总金额 = 各明细之和"
- 聚合之间通过 ID 引用，不直接持有对象引用
- 聚合尽量设计得小，避免锁竞争


🎯 练习：在你们的系统中找出 2-3 个聚合根，画出聚合边界图


---
layout: two-cols
---
# 6. 领域服务 & 仓储

### 领域服务（Domain Service）
当一个操作**不自然属于**某个实体或值对象时使用

```java
// 转账涉及两个账户，不属于单个 Account
public class TransferService {
    public void transfer(
            Account from, Account to, Money amount) {
        from.withdraw(amount);
        to.deposit(amount);
    }
}
```
::right::
### 仓储（Repository）
封装持久化细节，让领域层不关心数据库

```java
public interface OrderRepository {
    Optional findById(OrderId id);
    void save(Order order);
}

// 基础设施层实现，领域层不感知具体技术
public class JpaOrderRepository
        implements OrderRepository {
    private final OrderJpaDao dao;

    public Optional findById(OrderId id) {
        return dao.findById(id.value())
            .map(OrderMapper::toDomain);
    }
}
```

---
layout: two-cols
---

# 分层架构与 DDD

```
├── domain/              # 领域层：核心业务逻辑
│   ├── model/           #   实体、值对象、聚合
│   ├── service/         #   领域服务
│   ├── event/           #   领域事件
│   └── repository/      #   仓储接口（不含实现）
├── application/         # 应用层：用例编排
│   └── OrderAppService.java
├── infrastructure/      # 基础设施层：技术实现
│   ├── persistence/     #   仓储实现、ORM
│   └── external/        #   第三方接口、防腐层
└── interfaces/          # 接口层：Controller、DTO
```

::right::

```java
// 应用层：编排用例，不含业务规则
@Service
public class OrderAppService {
    private final OrderRepository orderRepo;
    private final InventoryDomainService inventory;

    @Transactional
    public void submitOrder(SubmitOrderCommand cmd) {
        Order order = orderRepo.findById(cmd.orderId())
            .orElseThrow();

        inventory.reserve(order);  // 调用领域服务
        order.submit();            // 调用聚合根方法

        orderRepo.save(order);
    }
}
```


✅ 依赖方向：interfaces → application → domain ← infrastructure
（依赖倒置，领域层不依赖任何技术框架）


---
layout: two-cols
---

# 第2天第3部分技术设计实践任务

::left::

## 选择1 DDD

1. 与组员一起提炼项目的**通用语言表**（至少10个术语）
2. 画出项目的**限界上下文图**（可用 draw.io / Miro / Mermaid）
3. 识别至少 2 个**聚合根**，标注聚合边界
4. 用代码写出至少 1 个实体、1 个值对象、1 个聚合根示例
5. 确认技术方案（含 AI 算法模型如何融入领域模型）
6. 规划新技术学习

::right::

## 选择2 AI Agent  

1. 明确 Agent 核心目标和典型使用场景
2. 确定 Agent 能力范围，明确可做与不可做
3. 设计Agent架构
4. 设计工具调用方法
5. 设计多论交互状态管理与用户体验
6. 设计安全与合规
7. 规划新技术学习

🎤 学习成果：系统设计技术方案

