# 修改记录

## v1.0 (2026-05-19)

### 主页 Hero
- 中文名去掉斜体，改为正常样式 `.hero-cn-name`
- Badge 改成「祝我铮铮，祝我昂扬」，Playfair Display 斜体 + 深色彩渐变文字
- 右侧新增「最新动态」状态面板：顶部渐变条、脉冲绿点标题、彩色列表项、渐变竖线装饰、底部头像
- 头像支持 `assets/avatar.png` 图片加载，失败时回退到 CSS 绘制
- Hero 整体双栏网格 `1fr 280px`，平板以下自动单列

### 经历概览
- 去掉「目标 2028 计算机硕士 · 清华大学」项
- 改为 3 列均匀排布
- 每个经历卡片左侧加 3px 彩色竖线（绿/粉/黄）

### 最新动态面板
- 加长 `min-height: 420px`
- 列表项间距加大，hover 有 radial-gradient 波澜扩散效果
- 底部头像 hover 放大+微旋转

---

## Git 初始化命令（在 personal-site 目录下执行）

```bash
cd personal-site
git init
git add .
git commit -m "feat: initial personal site with hero, projects, experience, blog"
```
