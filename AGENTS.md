# Repository Guidelines

## 项目结构与模块组织
- 核心游戏逻辑位于 `src/game.py`（单入口脚本，`main()` 启动）。
- 图片资源位于 `assets/images/`，统一使用英文文件名（如 `player_main.png`、`enemy_basic.png`、`map_1.png`）。
- 如后续复杂度上升，优先在 `src/` 下拆分模块（例如 `src/entities.py`、`src/ui.py`）。

## 构建、测试与开发命令
- 创建并激活虚拟环境：
  - `python3 -m venv .venv && source .venv/bin/activate`
- 安装依赖：
  - `pip install pygame`
- 本地运行游戏：
  - `python3 src/game.py`
- 提交前快速语法检查：
  - `python3 -m py_compile src/game.py`

## 代码风格与命名规范
- 遵循 PEP 8，使用 4 空格缩进，函数职责清晰。
- 变量/函数使用 `snake_case`，常量使用 `UPPER_SNAKE_CASE`。
- 注释保持简短、解释意图，避免重复代码字面含义。
- 资源文件名当前包含中文和空格；除非同步更新所有加载路径，否则不要随意重命名。

## 测试规范
- 当前无完整自动化测试；每次改动至少执行：
  - `python3 -m py_compile src/game.py`
  - 启动游戏并验证核心流程（移动、射击、UI 文本、资源加载）。
- 新增复杂逻辑时，建议使用 `pytest`，在 `tests/` 下添加 `test_<feature>.py`。

## 提交与合并请求规范
- 该目录当前无本地 Git 历史，建议统一采用：
  - `type(scope): 简短说明`（示例：`feat(player): 增加冲刺冷却`）。
- 单次提交聚焦单一功能或修复，必要时在提交说明中附验证方法。
- PR 建议包含：
  - 改动内容与原因
  - 运行/验证方式（如 `python3 src/game.py`）
  - 涉及可视化改动时附截图或短视频
  - 关联任务或 Issue 编号（如有）

## 安全与配置建议
- 避免硬编码绝对路径，统一使用相对脚本目录的 `os.path.join`。
- 谨慎管理二进制资源：控制图片体积，避免重复素材。
