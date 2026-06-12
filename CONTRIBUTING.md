# 山肴海错设计系统 · 贡献指南

> 感谢你考虑为山肴海错设计系统做出贡献。  
> 本指南适用于**人类贡献者**与 **AI Agent**，旨在保持设计系统的一致性、简洁性与高质量。

---

## 核心原则

所有贡献必须遵循设计系统的三大基石：

1. **克制** — 不添加多余装饰或冗余规则。
2. **精确** — 严格遵守 8px 网格、单强调色等原子规范。
3. **流畅** — 响应式、动效 ≤300ms、深色模式适配。

新增内容若无法从现有令牌推导，需提供充分理由。

---

## 可以贡献什么

| 类型 | 说明 | 示例 |
|------|------|------|
| 设计令牌 | 新增颜色、间距刻度、字号比例等原子变量 | 添加 `--ss-color-success` |
| 组件 | 新的 UI 组件（按钮、卡片、表格等）及其 CSS 规则 | 添加 `日期选择器` 组件 |
| 规则 | 布局、响应式、无障碍等条件逻辑 | 添加 `print` 媒体查询规则 |
| 文档 | `DESIGN.md`、`SKILL.md`、`README.md` 等文件的修正与完善 | 修正拼写错误、补充示例 |
| 自检清单 | 新增检查项或验证命令 | 补充性能检查项 |
| 示例 | 在 `examples/` 目录下新增使用示例 | 展示组件库在真实场景中的应用 |

---

## 贡献流程

### 1. 提出问题（可选）

在开始工作前，可先创建 **Issue** 讨论：

- 说明你要解决的问题或新增的功能
- 附上使用场景或设计草稿
- 等待维护者反馈后再动手，避免无效工作

### 2. 拉取仓库 & 创建分支

```bash
git clone https://github.com/shanyaohaicuo/design-system.git
cd design-system    
git checkout -b feature/your-feature-name
```

### 3. 实施更改

- **保持与现有规范一致**：参考 `DESIGN.md` 中的令牌、命名、代码风格。
- **新增组件**：必须包含 HTML 结构、CSS 样式、深色模式适配、响应式断点处理。
- **修改令牌**：需同步更新 `DESIGN.md` 和 `tokens.json`。
- **文档更新**：若新增功能影响使用方式，必须更新相应 `.md` 文件。
- **自检**：运行 `references/checklist.md` 中的 P0 和 P1 检查项。

### 4. 提交代码

```bash
git add .
git commit -m "feat: 添加日期选择器组件"
git push origin feature/your-feature-name
```

提交信息格式：

- `feat:` 新功能/组件
- `fix:` 修复错误
- `docs:` 文档更新
- `style:` 代码格式调整
- `refactor:` 重构
- `test:` 测试相关
- `chore:` 构建/工具变动

### 5. 创建 Pull Request

- 标题简明扼要，如“添加日期选择器组件”
- 内容需说明：
  - 解决了什么问题（关联 Issue 编号）
  - 主要变更内容
  - 自检结果（附截图或命令输出）
  - 是否需要更新 `CHANGELOG.md`

### 6. 审核与合并

- 至少一位维护者会审核 PR。
- 若涉及破坏性变更或设计争议，将在 PR 中讨论并达成共识。
- 通过后由维护者合并并更新 `CHANGELOG.md`。

---

## 对于 AI Agent 的特别说明

- **提交方式**：Agent 可通过创建 Pull Request 或提交规则建议（YAML/JSON）来贡献。
- **审核要求**：Agent 生成的规则、组件或令牌**必须附带人类审核**，不得自动合并。
- **自检强制**：Agent 在提交前必须运行 `checklist.md` 中的 P0 所有项，并输出检查结果。
- **命名与格式**：生成的 CSS 类名须遵循 `ss-` 前缀（如 `.ss-datepicker`），变量统一使用 `--ss-*`。

---

## 开发环境

本仓库无强制构建工具。如果你需要预览组件：

- 直接使用 HTML/CSS 编写，在浏览器中打开即可。
- 推荐使用 [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 等本地服务器。

---

## 行为准则

请参阅 [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md)。  
简而言之：尊重、包容、协作，禁止任何形式的骚扰或攻击。

---

## 获得帮助

如有任何疑问，请：

- 在 [Issues](https://github.com/shanyaohaicuo/design-system/issues) 中提问
- 通过邮件联系维护组（待补充）

再次感谢你的贡献！
