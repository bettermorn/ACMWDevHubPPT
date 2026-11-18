---
class: repo-slide
---

# 项目仓库结构

```text
repository-root/
├── docs/                                   # 项目文档
│   ├── requirements/                       # 需求文档（规格、用户故事、验收标准）
│   │   ├── problem_definition.md           # 问题定义（背景、痛点、目标、范围）
│   │   ├── functional_spec.md              # 功能需求规格说明
│   │   ├── nonfunctional_spec.md           # 非功能需求（性能、安全、可用性）
│   │   └── user_stories.md                 # 用户故事与验收标准
│   ├── algorithm/                          # 算法说明（推导、复杂度、参数）
│   │   └── research.md                     # 技术调研与选型依据
│   ├── software/                           # 软件设计（架构、接口、模块）
│   │   ├── prototype/                      # 原型设计（线框图、交互稿）
│   │   ├── architecture.md                 # 系统架构说明
│   │   ├── code_quality.md                 # 代码质量
│   │   ├── code_review.md                  # 代码评审
│   │   └── deployment.md                   # 系统部署
│   ├── mgmt/                               # 项目管理
│   │   ├── communication_mgmt_plan.md      # 沟通管理计划
│   │   └── risk_mgmt_plan.md               # 风险管理计划
│   └── retrospection/                      # 复盘总结与经验沉淀
├── code/                                   # 源码
│   ├── backend/                            # 后端服务（API、业务逻辑、数据访问）
│   ├── frontend/                           # 前端应用（页面、组件、状态管理）
│   └── core_engine/                        # 核心引擎（算法实现、公共库）
└── tests/                                  # 测试
    ├── unit/                               # 单元测试
    ├── integration/                        # 集成测试
    └── XXXagent_demo_user_test             # 用户测试
```

<style>
/* 所有规则限定在 .repo-slide，只影响本页 */

/* 页面：纵向 flex，标题在上，代码块占满剩余空间 */
.repo-slide.slidev-layout,
.repo-slide {
  display: flex !important;
  flex-direction: column !important;
  padding: 1.2rem 1.8rem 1rem !important;
  height: 100% !important;
  box-sizing: border-box !important;
}

/* 标题：保持 heading 1 的正常观感 */
.repo-slide h1 {
  font-size: 1.8rem !important;
  line-height: 1.25 !important;
  font-weight: 700 !important;
  margin: 0 0 0.5rem !important;
  padding: 0 !important;
  flex: 0 0 auto !important;
}

/* 代码块容器：填满剩余高度和宽度 */
.repo-slide .slidev-code-wrapper,
.repo-slide .slidev-code-wrapper > div,
.repo-slide pre.slidev-code {
  flex: 1 1 auto !important;
  width: 100% !important;
  min-height: 0 !important;
}
.repo-slide .slidev-code-wrapper {
  display: flex !important;
  flex-direction: column !important;
  margin: 0 !important;
}

.repo-slide pre,
.repo-slide .slidev-code,
.repo-slide .shiki {
  width: 100% !important;
  height: 100% !important;
  margin: 0 !important;
  padding: 0.6em 0.9em !important;
  box-sizing: border-box !important;
  overflow: hidden !important;
  font-size: 1.55vh !important;
  line-height: 1.32 !important;
}

.repo-slide pre code {
  font-size: inherit !important;
  line-height: inherit !important;
  display: block !important;
}
</style>


----

# 总结

反思在完成以下学习目标过程的优点、不足和进一步发展计划

1. 运用设计思维完成软件产品设计；
2. 在软件开发生命周期各环节圆满完成任务；
3. 运用AI与算法模型解决复杂问题；
4. 在作品实现过程中做好项目管理；
5. 发展支撑性工程素养。

谢谢
