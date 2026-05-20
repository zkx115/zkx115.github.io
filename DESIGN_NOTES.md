# 邹凯璇个人网站 — 设计上下文与修改指南

> 用于指导后续所有修改，避免重复确认。

---

## 一、设计系统

### 配色（OKLCH，支持暗色模式）
| Token | 值 | 用途 |
|-------|-----|------|
| `--c-pink` | oklch(88% 0.06 355) | 标签、装饰 |
| `--c-green` | oklch(82% 0.10 155) | 主强调色、dot |
| `--c-yellow` | oklch(87% 0.12 85) | 标签、装饰 |
| `--c-mint` | oklch(88% 0.08 180) | 标签 |
| `--c-lavender` | oklch(83% 0.07 285) | 标签 |

### 字体
- **Display**: Playfair Display（标题、艺术字）
- **Body**: Inter（正文）
- **Mono**: JetBrains Mono（标签、日期）

### 圆角
- `--r-lg: 20px` — 卡片、面板
- `--r-xl: 32px` — 大区块
- `100px` — pill 标签、badge

---

## 二、页面结构

### 主页 `index.html`
```
Nav (fixed, blur backdrop)
├── Hero (100svh, blur orbs + grid overlay)
│   ├── 左侧：badge + 标题 + 副标题 + CTA + 技能标签
│   └── 右侧：最新动态面板（status card）
├── 精选项目（4 cards, 2x2 grid, first featured spans 2 cols）
├── 经历概览（3列均匀 strip, 每项左侧彩色竖线）
├── 近期博客（4 rows）
├── Contact
└── Footer
```

### 其他页面
- `projects.html` — 6 个项目卡片 + 过滤器
- `experience.html` — 时间线 + 技能标签 + 竞赛/证书
- `blog/index.html` — Jekyll Satellite 风格侧边栏 + 文章列表

---

## 三、关键已确定的设计决策

### 1. Badge「祝我铮铮，祝我昂扬」
- **字体**: Playfair Display, italic, weight 700
- **颜色**: 深色 oklch 渐变（粉→黄→绿，低明度高彩度）
- **阴影**: `text-shadow: 0 1px 8px oklch(60% 0.05 250 / 0.25)` 提升对比
- **背景**: 保持原 badge 样式不变（浅色背景+边框）
- ⚠️ 不可改回浅色渐变，会与 hero 背景融合导致看不清

### 2. Hero 双栏布局
- **网格**: `grid-template-columns: 1fr 280px`
- **右侧面板宽度**: 固定 280px
- **响应式**: 平板以下（≤768px）自动变单列，面板居中

### 3. 最新动态面板
- **最小高度**: `min-height: 420px`
- **顶部**: 3px 渐变条（绿→粉→黄）
- **左侧竖线**: 渐变装饰线，从列表顶部贯穿到底部分隔线
- **列表项间距**: `gap: var(--space-4)`（较大）
- **Hover 效果**: radial-gradient 波澜扩散（从鼠标位置向外扩散）
- **底部头像**:
  - 优先加载 `assets/avatar.png`（用户可替换自己的图片）
  - 加载失败时回退到 CSS 绘制版本
  - Hover: `scale(1.08) rotate(-3deg)` + 阴影加深

### 4. 经历概览（Experience Strip）
- **列数**: 3 列均匀（`repeat(3, 1fr)`）
- **已去掉**: 「目标 2028 计算机硕士 · 清华大学」项
- **左侧竖线**: 每项 `border-left: 3px solid` 对应 dot 颜色
- **项之间**: 竖线分隔（`.exp-divider`，1px 灰色）

### 5. 用户明确的偏好
- ✅ 喜欢当前 hero 背景（粉绿黄模糊球 + 网格 overlay），不可改
- ✅ 喜欢「祝我铮铮，祝我昂扬」这句话，字体用艺术斜体
- ✅ 不喜欢太小的间距，喜欢留白
- ✅ 喜欢 hover 有动效反馈（波澜、放大等）
- ✅ 希望用自己的头像图片替换 CSS 绘制版
- ❌ 不喜欢斜体中文名（已改为正常样式）
- ❌ 不喜欢有空缺/不均匀布局（经历已改为3列均匀）

---

## 四、后续修改速查

### 替换头像图片
把任意图片放到 `personal-site/assets/avatar.png`，自动生效（支持 PNG/JPG/WebP）。

### 修改最新动态内容
编辑 `index.html` 中 `.hero-status .status-list` 内的 `<li>` 项即可。

### 修改 badge 文字
编辑 `index.html` 中 `.hero-badge .badge-text`。

### 添加/删除经历项
编辑 `index.html` 中 `.exp-strip` 内的 `.exp-item` 块。注意保持 3 列需有 3 的倍数个项。

---

## 五、技术栈
- 纯 HTML + CSS + 原生 JS
- 无框架依赖
- 设计 token 全用 CSS 自定义属性（`--*`）
- 暗色模式通过 `[data-theme="dark"]` 切换
- 动效用 CSS `@keyframes` + `transition`

---

*最后更新: 2026-05-19*
