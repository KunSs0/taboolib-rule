# Repository Guidelines

## 项目结构与模块组织
本仓库围绕 TabooLib 规则文档维护，核心内容位于 `docs/`，按照 Basic、Bukkit、Configuration 等模块拆分成独立 Markdown 文件，便于针对性更新。
示例 Kotlin 源码集中在 `example/command/1` 与 `example/database/1`，用于演示命令路由、数据库访问等高级用法；新增示例时按现有数字目录分层，保证主题清晰。
根目录保留 `README.md`、`LICENSE` 等信息文件，不在此处存放源码，避免和文档混杂。

## 构建、测试与开发命令
仓库以文档为主，不提供直接构建脚本；验证 Kotlin 片段时，请在本地 TabooLib 插件工程中同步示例文件后执行 `./gradlew build` 校验基础编译。
若需要运行单元测试或 Kether 脚本验证，仍在宿主工程内使用 `./gradlew test`，确保示例与文档描述一致。
对 Markdown 文档建议执行 `npx markdownlint-cli docs/**/*.md`，快速捕捉标题层级和代码块语法问题。

## 代码风格与命名约定
Markdown 文档使用一级标题展示主题、二级标题对应模块，列表层级不超过三级，链接采用相对路径。
Kotlin 示例遵循四空格缩进、UpperCamelCase 类名、lowerCamelCase 函数与属性命名；扩展方法需要清晰的接收者前缀。
文档中的命令和代码块使用 ```kotlin``` 或 ```shell``` 标识，保持行宽不超过 100 字符。

## 测试指引
更新数据库、命令等示例时，请编写最小复现场景并在 Paper 服务端加载，确认初始化和权限配置正确。
文档应注明外部依赖版本，必要时在示例目录追加 `README.md` 记录测试步骤和期望输出。
若调整配置格式，附带 `docs/Configuration.md` 中的对比表，并在宿主工程运行一次 `./gradlew runPaper` 或自定义启动脚本验证加载日志。

## 提交与 Pull Request 规范
历史提交多采用中文前缀与简要说明（例如 “更新项目模块文件和数据库文档”），建议继续使用祈使句描述主要变更，并在首句标明影响范围。
PR 需提供：变更摘要、涉及模块列表、验证步骤（含命令输出要点），如更新示例请附 IDE 截图或服务器日志片段。
提交前确认 Markdown lint、Gradle 构建及相关测试均已通过，并在讨论区同步潜在破坏性调整以提前获取审阅反馈。

## 文档与示例维护建议
扩展新章节时优先复用现有排版模板，在 `docs/` 中按模块首字母排序，方便索引。
示例目录建议保持数字加主题的命名方式，例如 `example/database/3-redis`，并在文档中引用对应路径。
