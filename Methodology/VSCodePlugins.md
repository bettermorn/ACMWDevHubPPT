# Python VS Code Python代码质量检查全景指南
在VS Code中，检查Python代码质量（包括语法错误、风格不一致、潜在Bug、安全漏洞和类型错误）是一个非常成熟且高效的工程化流程。
目前，VS Code已经将原先集成的Python工具拆分成了独立的、轻量级的插件。为了获得最佳的代码质量检查效果，建议采用组合拳的方式。

## 一、 核心插件推荐（按功能分类）
为了实现全面的代码质量监控，我们可以将检查任务分为四个维度：静态代码分析（Linting）、代码格式化（Formatting）、类型检查（Type Checking） 和 安全与重构（Security & Refactoring）。
1. 静态代码分析（Linting）- 寻找 Bug 和不规范
- Ruff (强烈推荐 ⭐⭐⭐⭐⭐)
○介绍：目前 Python 社区最火的 Linter。它是用 Rust 编写的，速度比传统的 Flake8 快 10-100 倍。
○功能：它不仅能替代 Flake8（代码风格），还能替代 isort（导入排序）、unused-imports、bandit（部分安全检查）等数十个工具。
○优点：极速、开箱即用、支持自动修复（Autofix）。
- Pylint (传统经典 ⭐⭐⭐⭐)
○介绍：最老牌、最严格的 Python Linter。
○优点：检查极其细致，能发现非常隐蔽的逻辑错误和重构建议。
○缺点：速度较慢，对大型项目可能会有卡顿；默认规则有些严苛，需要较多配置。
2. 代码格式化（Formatting）- 统一代码风格
- Black Formatter (推荐 ⭐⭐⭐⭐⭐)
○介绍：被称为“无妥协的 Python 代码格式化工具”。
○功能：强制执行统一的格式（比如双引号、固定的折行逻辑），让团队代码看起来像出自一人之手。
- Ruff (格式化功能 ⭐⭐⭐⭐⭐)
○最新动态：Ruff 现在也集成了格式化功能（Ruff Format），完全可以替代 Black，且速度极快。
3. 静态类型检查（Static Type Checking）- 减少类型错误
- Pylance (必装 ⭐⭐⭐⭐⭐)
○介绍：微软官方的 Python 语言服务器，内置了 Pyright 类型检查器。
○功能：提供极速的自动补全、参数提示、以及实时的类型检查（比如把 str 传给了需要 int 的函数时会报错）。
- Mypy (专业级 ⭐⭐⭐⭐)
○介绍：Python 官方标准的静态类型检查器（需安装 Mypy 插件）。适合对类型安全要求极高的项目。
4. 高级重构与安全检查
- SonarLint (⭐⭐⭐⭐)
○功能：大名鼎鼎的 SonarQube 的本地版。除了检查 Python 语法，还能检测出“认知复杂度过高”、“安全漏洞（SQL 注入等）”、“代码异味（Code Smell）”。
- Sourcery (⭐⭐⭐⭐)
○功能：AI 辅助的重构工具。它会直接在代码行旁给出重构建议（例如：将多行循环简化为列表推导式、合并 redundant 的 if 语句）。

## 二、 黄金组合配置方案
以下推荐两套配置方案：“现代极速流”（推荐） 和 “传统严谨流”。
### 方案 A：现代极速流（Ruff + Pylance）—— 适合 90% 的开发者
这是目前最推荐的配置，速度极快，体验极佳。
1.在 VS Code 中安装以下插件：

○Python (Microsoft)
○Pylance (Microsoft)
○Ruff (Astral Software)
2.配置自动修复与保存时格式化：
打开 VS Code 的 settings.json（快捷键：Ctrl + Shift + P -> 输入 Preferences: Open User Settings (JSON)），添加以下配置：

```
{
    // 启用 Pylance 的基本类型检查
    "python.analysis.typeCheckingMode": "basic", 

    // 设置 Ruff 为默认的 Linter 和 Formatter
    "[python]": {
        "editor.defaultFormatter": "charliermarsh.ruff",
        "editor.formatOnSave": true, // 保存时自动格式化
        "editor.codeActionsOnSave": {
            "source.fixAll.ruff": "explicit", // 保存时自动修复可以修复的错误
            "source.organizeImports.ruff": "explicit" // 保存时自动整理导包顺序
        }
    },
    // 让 Ruff 提示所有兼容的规则
    "ruff.lint.args": ["--select=E,F,UP,B,SIM,I"] 
}
```

### 方案 B：传统经典流（Black + Pylint + Mypy）
适合已有老项目，或者对严格度有极高要求的团队。
1.安装插件：

○Python, Pylance
○Black Formatter (Microsoft)
○Pylint (Microsoft)
○Mypy Type Checker (Microsoft)
2.settings.json 配置：

```
{
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter",
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.organizeImports": "explicit"
        }
    },
    "pylint.importStrategy": "fromEnvironment",
    "mypy.run": "onType" // 实时进行 Mypy 类型检查
}
```

## 三、 深度定制：使用项目配置文件（最佳工程实践）
为了防止“在我的电脑上没报错，在同事电脑上报错”的情况，不建议将所有规则写在 VS Code 的全局设置中。更好的做法是在项目根目录下创建配置文件，这样所有团队成员（以及 CI/CD 流程）都能共享同一套标准。
1. 使用 pyproject.toml（推荐，现代 Python 项目标准）
在项目根目录下创建 pyproject.toml，写入以下内容（以 Ruff 为例）：
[tool.ruff] # 目标 Python 版本 target-version = "py310" # 每行最大长度 line-length = 88  [tool.ruff.lint] # 启用的规则集 # E/W: pycodestyle (PEP8) # F: Pyflakes (语法错误) # I: isort (导入顺序) # B: flake8-bugbear (潜在逻辑Bug) # C4: flake8-comprehensions (更优的集合/列表表达) # UP: pyupgrade (升级到现代Python语法) select = ["E", "W", "F", "I", "B", "C4", "UP"]  # 忽略特定规则 ignore = ["E501"] # 忽略单行长度超标警告  [tool.ruff.lint.per-file-ignores] # 测试文件中允许使用 assert 语句和未使用的导入 "tests/*" = ["S101", "F401"] VS Code 的 Ruff 插件会自动读取这个文件，并在编辑器中实时呈现对应的警告或错误。

## 四、 如何在 VS Code 中查看和处理质量问题？
1.波浪线提示： 
○红色波浪线：语法错误或严重 Bug（由 Pylance/Ruff 报出）。
○黄色波浪线：代码规范问题或潜在隐患（由 Ruff/Pylint 报出）。
2.问题面板（Problems Panel）： 
○使用快捷键 Ctrl + Shift + M（Mac 上是 Cmd + Shift + M）打开“问题”面板，这里会列出当前项目或文件中的所有警告和错误，点击即可跳转到对应行。
3.快速修复（Quick Fix）： 
- 将光标移到有黄色波浪线的代码上，按下 Ctrl + . (Mac: Cmd + .)，VS Code 会弹出修复建议。如果是 Ruff，可以直接点击“Autofix this issue”。
总结建议
●新手/追求效率者：直接安装 Ruff 和 Pylance，开启 formatOnSave，体验极佳。
●团队规范严格者：在项目根目录下配置 pyproject.toml，并结合 Git 的 pre-commit 钩子，确保不合规的代码绝对无法提交。
