# 课件说明

本科《软件创新工程实践课程》课件 同样适用于本科《软件新技术创新实践课程》


# 项目仓库结构

```text
repository-root/
├── docs/                           # 项目文档
│   ├── requirements/                # 需求文档（需求规格、用户故事、验收标准）
│   │   ├── problem_definition.md      # 问题定义（背景、痛点、目标、范围边界）
│   │   ├── functional_spec.md         # 功能需求规格说明
│   │   ├── nonfunctional_spec.md      # 非功能需求规格说明（性能、安全、可用性等）
│   │   └── user_stories.md            # 用户故事与验收标准
│   │
│   ├── algorithm/                   # 算法说明（公式推导、复杂度分析、参数说明）
│   │   └── research.md                # 技术调研（候选方案对比、论文/资料整理、选型依据）
│   │
│   ├── software/                    # 软件设计（架构图、接口文档、模块设计）
│   │   ├── prototype/                 # 原型设计（线框图、交互原型、UI/UX 草稿）
│   │   └── architecture.md            # 系统架构说明文档
│   │   └── code_quality.md            # 代码质量
│   │   └── code_review.md             # 代码评审
│   │   └── deployment.md              # 系统部署
│   │  
│   ├── mgmt/                         # 项目管理（沟通管理、风险管理）
│   │   ├── communication_mgmt_plan.md # 沟通管理计划
│   │   └── risk_mgmt_plan.md          # 风险管理计划
│   │
│   └── retrospection/                # 复盘总结（迭代回顾、事故复盘、经验沉淀）
│
├── code/                            # 源码
│   ├── backend/                      # 后端服务（API、业务逻辑、数据访问）
│   ├── frontend/                     # 前端应用（页面、组件、状态管理）
│   └── core_engine/                  # 核心引擎（算法实现、公共库、被前后端复用）
│
└── tests/                           # 测试
    ├── unit/                         # 单元测试
    └── integration/                  # 集成测试
    └── XXXagent_demo_user_test       # 用户测试
```

