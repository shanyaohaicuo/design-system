# 山肴海错设计系统 · SKILL.md

> **克制 · 精确 · 流畅**  
> Agent 最小执行指南。完整规范见 [`DESIGN.md`](./DESIGN.md)。

---

## 身份标识

```yaml
name: 山肴海错设计系统
kind: design-system
version: 1.0.0
locale: zh-CN
source: ./DESIGN.md
tokens: ./tokens.json
```

---

## 输入契约

执行前必须向用户确认以下信息：

| 字段 | 必需性 | 示例 |
|------|--------|------|
| 项目类型 | 必须 | 落地页 / 仪表盘 / 幻灯片 |
| 目标平台 | 必须 | 响应式网页 / 桌面 / 移动 |
| 目标用户 | 推荐 | 投资人 / 企业采购者 |
| 品牌背景 | 推荐 | 已有品牌色 / 由系统决定 |
| 内容规模 | 推荐 | 1个落地页 + 3个子页面 |

---

## 核心原则

1. **克制** — 不做多余装饰
2. **精确** — 8px 网格，禁止硬编码
3. **流畅** — 响应式三断点，动效 ≤300ms

**绝对禁止**：高饱和渐变、双强调色、圆角>12px、emoji图标、非8px数值、移动端hover。

**设计令牌**：所有样式值必须引用 `--ss-*` 变量。完整的颜色（含深色模式）、间距、字体、圆角、阴影、动效、断点定义见 [`tokens.json`](./tokens.json)。

---

## 工作流程

1. 加载 `./DESIGN.md` 和 `./tokens.json`
2. 确认输入契约中的缺失信息
3. 使用 `tokens.json` 中的变量和 `DESIGN.md` 中的组件规范生成 UI
4. 运行 [`references/checklist.md`](./references/checklist.md) 自检
5. 输出 HTML 文件（一个场景一个文件）

---

## 输出约定

- 每个独立界面一个 HTML 文件
- 多页项目：`index.html` 为启动页
- 幻灯片：使用 `<section class="slide">`

---

## 相关文件

| 文件 | 用途 |
|------|------|
| `DESIGN.md` | 完整规范（组件、规则、反模式） |
| `tokens.json` | 机器可读设计令牌（颜色、间距、字体等） |
| `README.md` | 项目介绍 |
| `references/checklist.md` | 详细自检清单 |