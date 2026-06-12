# 山肴海错设计系统 — DESIGN.md

> **克制 · 精确 · 流畅**  
> 8px 网格 · 单主色 · 响应式三断点 · 深色模式内置  
> 本文件仅包含不可推导的原子规范，其余可由此生成。

**Source-backed**: 所有具体数值均定义在 [`tokens.json`](./tokens.json) 中，并通过 CSS 自定义属性 `--ss-*` 引用。

---

## 品牌性格

| 维度 | 说明 |
|------|------|
| 克制 | 不做多余装饰。无法说出“为何存在”则删除。 |
| 精确 | 所有间距、尺寸遵守 8px 网格。禁止硬编码。 |
| 流畅 | 响应式三端，动效 ≤300ms，支持 `prefers-reduced-motion`。 |

**反面特征**：高饱和渐变、圆角 >12px、手绘风格、emoji 图标、双强调色、暖色米白/桃色/粉色背景（除非品牌要求）。

---

## 颜色（Color）

**来源**: [`tokens.json`](./tokens.json) 中的 `color` 对象（含浅色与深色模式值）。

核心变量：

```css
--ss-color-primary:        #1A1A1A;
--ss-color-surface:        #FFFFFF;
--ss-color-surface-elevated: #F5F5F5;
--ss-color-text-secondary: #666666;
--ss-color-border:         #E5E5E5;
--ss-color-accent:         #7A5C3B;   /* 唯一强调色 */
--ss-color-disabled:       #CCCCCC;
```

深色模式：`@media (prefers-color-scheme: dark)` 覆盖上述变量（值见 `tokens.json` 中的 `dark` 映射）。  
对比度：所有文字与背景组合满足 WCAG AA（≥4.5:1）。

---

## 排版（Typography）

**来源**: [`tokens.json`](./tokens.json) 中的 `typography` 对象。

**字体栈**（不加载 web 字体）：

```css
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
```

**字号比例**（1.25 倍韵律，单位 px）：

| 级别 | 大小 | 行高 | 应用 |
|------|------|------|------|
| H1 | 40 | 1.25 | 页面主标题 |
| H2 | 32 | 1.25 | 板块标题 |
| H3 | 24 | 1.25 | 章节标题 |
| H4 | 20 | 1.25 | 小标题 |
| 正文 | 16 | 1.5 | 桌面基础 |
| 小号 | 14 | 1.5 | 移动端基础 / 辅助 |
| 标记 | 12 | 1.4 | 标签、元数据 |

基础字号：桌面 16px，移动端（<640px）14px。  
字重：标题 600–700，正文 400，辅助 400–500。

---

## 间距（Spacing）

**来源**: [`tokens.json`](./tokens.json) 中的 `spacing` 对象。

**刻度**（px）：`4, 8, 12, 16, 24, 32, 48, 64, 80`  
任何 `margin`、`padding`、`gap` 必须取自此列表。

---

## 圆角与阴影

**圆角**：全局统一一个主值（≤12px），禁止混用。  
推荐：按钮/输入框 4px，卡片 8px，弹窗 12px。

**阴影**（仅用于 hover/active，禁止彩色阴影）：

```css
--ss-shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--ss-shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.05);
```

---

## 动效（Motion）

**来源**: [`tokens.json`](./tokens.json) 中的 `motion` 对象。

- 时长 ≤300ms（`--ss-duration`）
- 缓动：`cubic-bezier(0.2, 0.9, 0.4, 1.1)`（`--ss-easing`）
- 降级：必须包含 `@media (prefers-reduced-motion: reduce) { transition: none; }`

---

## 语音与语调（Voice）

本设计系统的语音规范（无令牌来源，属于品牌原则）：

- **语气**：冷静、精确、中性，避免浮夸或过度热情。
- **人称**：使用“你”而非“您”，保持尊重但不疏远。
- **标点**：句尾使用句号；列表项末尾不加标点（除非完整句子）。
- **文案**：禁止 emoji 作为图标，使用纯文本或 SVG 符号。

---

## 响应式断点

| 断点 | 布局 | 导航 | 触摸目标 | 按钮宽度 |
|------|------|------|----------|----------|
| <640px | 单列 | 底部标签栏 | ≥44px | 100% |
| 640–1024px | 2列网格 | 侧边栏可选 | ≥40px | auto |
| >1024px | 多列（≤12） | 左侧固定侧边栏 | ≥38px | auto |

---

## 反模式（Anti-patterns）

| 类别 | 禁止内容 |
|------|----------|
| 数值 | 非 8px 网格硬编码（如 `13px`） |
| 颜色 | 未定义色值，尤其高饱和色（`#FF00FF` 等） |
| 强调色 | 同时使用两个以上 |
| 圆角 | >12px |
| 背景 | 渐变背景 |
| 图标 | emoji 作为图标 |
| 动效 | 时长 >300ms |
| 交互 | 移动端 hover 作为主要交互 |

---

## 设计决策规则

| 规则 ID | 条件 | 决策 |
|---------|------|------|
| R01 | 任何间距 | 必须使用 `--ss-spacing-scale` 中的值，禁止硬编码 |
| R02 | 按钮 hover | 背景色亮度降低 10% (`filter: brightness(0.9)`) |
| R03 | 移动端（<640px） | 所有按钮宽度 100%，导航切换为底部标签栏 |
| R04 | 深色模式 | 必须提供 `@media (prefers-color-scheme: dark)` 变量覆盖 |
| R05 | 强调色使用 | 同一屏幕不超过 2 次 |
| R06 | 圆角 | 全局统一 4px 或 8px，禁止混用 |

---

## 扩展规则

- **新增组件**：先从现有令牌推导，必须支持深色模式。
- **辅助色**（成功/警告/错误）：基于 accent 色使用 `color-mix()` 派生，禁止高饱和色。

---

*本文件为唯一权威来源。所有样式值必须引用 `--ss-*` 变量。变更需同步更新 `tokens.json`。*