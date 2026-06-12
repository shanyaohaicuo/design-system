# 山肴海错设计系统

> **克制 · 精确 · 流畅**  
> 一套面向 Open Design 与 AI Agent 的设计系统。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## Product Overview

山肴海错是一个极简、高级、响应式的设计系统，基于 8px 网格、单强调色灰度体系，内置深色模式，专为人类设计师和 AI Agent 构建。

- **克制的设计哲学** – 不做多余装饰，每个元素都有明确目的。
- **精确的原子规范** – 所有间距、颜色、字体都来源于 `tokens.json` 单一事实源。
- **流畅的跨端体验** – 响应式三断点 (手机/平板/桌面)，动效 ≤300ms。

## Product Context

本系统适用于：

- 需要快速搭建品牌一致界面的开发团队
- 希望引入设计规范的独立开发者
- AI Agent（如 Claude Code）自动生成符合约束的 UI
- 开源社区贡献组件和规则

## Source / Context References

| 文件 | 用途 |
|------|------|
| [`DESIGN.md`](./DESIGN.md) | 完整的设计原则、组件规范、反模式 |
| [`tokens.json`](./tokens.json) | 机器可读的设计令牌（颜色、间距、字体等） |
| [`SKILL.md`](./SKILL.md) | Agent 执行最小指南 |
| [`references/checklist.md`](./references/checklist.md) | 发布前自检清单 |
| [`CONTRIBUTING.md`](./CONTRIBUTING.md) | 贡献指南 |

## Package Contents

```plaintext
.
├── assets/                  # 静态资源 (可选)
├── build/                   # 保留的构建资产 (图标等)
│   ├── icon.png
│   └── tray_icon.png
├── ui_kits/                 # UI 套件演示
│   └── app/
│       ├── colors_and_type.css
│       ├── components/
│       │   ├── button.css
│       │   └── card.css
│       └── index.html
├── preview/                 # 预览卡片
│   └── brand-assets.html
├── examples/                # 示例页面 (可选)
├── DESIGN.md
├── README.md
├── SKILL.md
├── tokens.json
├── CONTRIBUTING.md
├── LICENSE
└── references/
    └── checklist.md
```

## Preview Manifest

生成的预览卡片 (位于 `preview/`)：

| 文件 | 目的 | 展示的资产/组件 |
|------|------|----------------|
| [`preview/brand-assets.html`](./preview/brand-assets.html) | 品牌资产预览 | 引用 `build/` 中的图标文件，展示强调色 |
| (未来可扩展: `preview/components.html`) | 组件库总览 | 所有核心组件 |

其他演示：

- **UI Kit 完整界面**: [`ui_kits/app/index.html`](./ui_kits/app/index.html) – 加载设计令牌和组件 CSS，展示按钮、卡片及组合使用。

## Preserved Assets / Fonts / Build Artifacts

- **`build/icon.png`** – 品牌图标 (1x1 透明占位符，实际可替换)
- **`build/tray_icon.png`** – 系统托盘图标
- 所有字体均为系统默认，未加载外部字体。

## Reuse or Review Workflow

### 直接复制令牌

将 `tokens.json` 中的 CSS 自定义属性拷贝到项目 `:root`。

### Agent 工作流 (Claude Code)

1. 加载 `DESIGN.md` 和 `tokens.json`
2. 根据 `SKILL.md` 的输入契约收集需求
3. 生成符合 `--ss-*` 变量的 HTML/CSS
4. 运行 `references/checklist.md` 自检
5. 输出最终文件

### 贡献新组件

阅读 `CONTRIBUTING.md`，提交 PR 并确保  - 通过自检清单。

## License

MIT © 山肴海错设计系统
