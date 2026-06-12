# 山肴海错 · 自检清单

> 输出每个 HTML 前逐项检查。**P0 必须全部通过**，否则不可发布。

---

## P0（阻塞级 — 必须通过）

| 检查项 | 快速验证 |
|--------|----------|
| 颜色引用自 `--ss-*` 变量，无硬编码 | `grep -n '#[0-9a-fA-F]' index.html \| grep -v 'var(--ss-'` 应无输出 |
| 间距属 8px 网格：`4,8,12,16,24,32,48,64,80` | `grep -nE '(margin\|padding\|gap):' index.html \| grep -vE '(auto\|0\|4px\|8px\|12px\|16px\|24px\|32px\|48px\|64px\|80px\|var\()'` 无输出 |
| 圆角 ≤12px | `grep -n 'border-radius' index.html \| grep -E '(1[3-9]\|[2-9][0-9])px'` 无输出 |
| 无 emoji 图标 | `grep -nP '[\x{1F300}-\x{1F9FF}]' index.html` 无输出（内容 emoji 除外） |
| 无渐变背景 | `grep -n 'gradient' index.html` 无输出 |
| 无高饱和色（`#FF00FF`、`#00FF00` 等） | 目视检查颜色值 |
| 移动端触摸目标 ≥44px | 检查 `<button>`、`<a>` 等元素的 `width/height` 或 `padding` |
| 深色模式已映射 | 存在 `@media (prefers-color-scheme: dark) { :root { ... } }` |
| 尊重 `prefers-reduced-motion` | 存在 `@media (prefers-reduced-motion: reduce) { *, *::before, *::after { transition-duration: 0s; } }` |
| 表格使用 `.table-wrap` | `class="table-wrap"` 包含 `</td>` |

---

## P1（推荐级 — 尽量通过）

| 检查项 | 说明 |
|--------|------|
| accent 色每屏 ≤2 次 | 搜索 `var(--ss-color-accent)` 出现次数 |
| 三断点 UI 正常 | 手动缩放浏览器至 <640、640–1024、>1024 |
| 动效时长 ≤300ms | 搜索 `transition-duration\|animation-duration`，最大值 ≤300ms |
| 字号使用 1.25 刻度（12/14/16/20/24/32/40） | 检查所有 `font-size` |
| 无外部 web 字体 | `@font-face` 和 Google Fonts 无引用 |
| 交互元素有 `:focus-visible` | 搜索 `focus-visible` |
| 按钮 hover 有反馈 | 检查 `.btn:hover` 有 `filter` 或 `background` 变化 |
| 移动端按钮宽度 100% | `@media (max-width: 639px) { .btn { width: 100%; } }` |
| 卡片 hover 有微阴影 | `.card:hover { box-shadow: var(--ss-shadow-sm); }` |
| 空状态有引导 | 无空白区域，有文本/占位符 |
| 页面 `<title>` 已填充 | 非空 |

---

## P2（加分项 — 可选）

- 输入框 focus 使用 accent 色 outline
- 表格行 hover 背景变化
- 标签用 `color-mix()` 从 accent 衍生
- 侧边栏导航有 hover/active 状态
- 移动端底部栏高度 56px，触摸目标 ≥44px
- 图片有 `alt` 属性
- 文件名清晰（非 `page1.html`）
- 无调试代码（`console.log`、`debugger`）

---

## 快速命令（一键检查 P0）

```bash
# 假设输出文件为 index.html
echo "=== 硬编码颜色 ===" && grep -n '#[0-9a-fA-F]' index.html | grep -v 'var(--ss-' || echo "✅ 通过"
echo "=== 非网格间距 ===" && grep -nE '(margin|padding|gap):' index.html | grep -vE '(auto|0|4px|8px|12px|16px|24px|32px|48px|64px|80px|var\()' || echo "✅ 通过"
echo "=== 圆角超标 ===" && grep -n 'border-radius' index.html | grep -E '(1[3-9]|[2-9][0-9])px' || echo "✅ 通过"
echo "=== emoji ===" && grep -nP '[\x{1F300}-\x{1F9FF}]' index.html || echo "✅ 通过"
echo "=== 渐变 ===" && grep -n 'gradient' index.html || echo "✅ 通过"
```

---

## 发布确认

- [ ] P0 全部 ✅
- [ ] P1 已评估（可豁免项已注明原因）
- [ ] 浅色 / 深色模式均预览
- [ ] 手机 / 平板 / 桌面三断点验证