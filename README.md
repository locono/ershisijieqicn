<a id="zh"></a>

# 廿四节气 · 中国人的时间美学

> 一个关于二十四节气的单文件科普网站：节气轮盘、七十二候、民俗养生、节气诗话。
> 全部内容写在一个 `index.html` 里，**零构建、零依赖、零网络请求**，双击即可打开。

![单文件](https://img.shields.io/badge/单文件-75%20KB-b89b6a) ![依赖](https://img.shields.io/badge/外部依赖-0-5c8f63) ![运行](https://img.shields.io/badge/运行方式-浏览器直接打开-4d6f8f)

**中文** | [English](#en)

---

## 页面结构

| 板块 | 锚点 | 内容 |
|---|---|---|
| 首屏 · 首页 | `#top` | 大标题、导语、快捷入口、「今日节气」卡片（进度环 + 氛围切换） |
| 节气轮盘 | `#wheel` | 560px SVG 轮盘，24 节气放射排布，四季分区着色，四正方位标注 |
| 二十四节气 | `#terms` | 24 张节气卡，按春夏秋冬筛选，今日节气有标记 |
| 七十二候 | `#hou` | 24 组 × 3 候，每候配一句白话释义 |
| 节气诗话 | `#poem` | 每节气撷一句古诗，共 24 首，注明出处 |
| 节气歌 | `#song` | 完整口诀与「上半年六廿一、下半年八廿三」注解 |

顶部导航：**首页 / 七十二候 / 节气诗话 / 节气歌**（滚动自动高亮当前板块）。

---

## 主要功能

### 内容

- **今日节气自动推算**：按系统日期算出当前节气、交节区间、太阳黄经、距下一节气天数、初候物候，全年任意一天都能正确落位
- **二十四节气全档案**：每个节气含释义、三候、民俗、养生、农事、诗句六项
- **七十二候**：如「群鸟养羞 · 百鸟储食备冬」
- **节气诗话**：24 首古诗名句，注明出处

### 交互

- **节气轮盘**：节气名沿半径放射排布（左半圈自动翻转 180° 保证可读）；点击任一节气展开右侧抽屉
- **详情抽屉**：ESC 关闭，左右方向键前后翻节气，底部有上一 / 下一节气按钮
- **开始巡览 / 回到今日**：每 1.6 秒自动推进一个节气，指针、氛围、粒子同步跟随
- **四季筛选**：二十四节气板块按春夏秋冬过滤
- **氛围切换**：今日卡底部「氛围 春夏秋冬」按钮，或点击轮盘任一节气，整站配色随之迁移
- **返回顶部**：右下角圆形悬浮按钮，滚动超过约 2/3 屏后浮现，点击平滑回顶
- **页脚邮箱**：点击复制 `imuse@163.com`

### 视觉与动效

- **四季氛围引擎**：`body[data-season]` 驱动全局强调色，四层全屏渐变交叉淡入（1.2s）

  | 春 | 夏 | 秋 | 冬 |
  |---|---|---|---|
  | `#5c8f63` | `#c1503f` | `#c08a2e` | `#4d6f8f` |

- **Canvas 四季粒子**：春·花瓣打着旋飘落 / 夏·斜雨丝 / 秋·落叶摆荡 / 冬·细雪。按屏宽取 34–110 个，DPR 适配，页面切后台自动暂停
- **首屏背景**：三团随季节变色的大光斑缓慢漂移（26–38s 循环）；巨型「節」字水印 90s 缓转
- **标题流光**：「一轮廿四节气」为渐变文字，每 7 秒扫过一道季节色流光
- **鼠标跟随柔光**：光标在首屏移动时一团强调色光晕跟随；标题反向微移、今日卡正向微移形成层次
- **轮盘立体**：鼠标视差 13° 带纵深；外围一圈缓慢旋转的虚线环；当前节气扇形持续脉冲发光
- **滚动视差**：首屏文字 0.22 倍速上移，光斑与水印渐隐离场
- **微交互**：今日卡呼吸浮动、印章缓慢缩放、按钮悬停上浮、诗卡竖线由短拉满、候条右移
- **入场动画**：首屏分层错峰淡入，网格按序入场（筛选时重播），节气歌逐句浮现

### 无障碍与降级

- `prefers-reduced-motion` 下关闭全部动画与粒子
- 数字滚动动画带 `setTimeout` 兜底，极端情况也落到正确数值
- 邮箱复制三级兜底：Clipboard API → 800ms 超时/失败 → `execCommand` → 再失败自动选中并提示

---

## 技术说明

- **单文件**：HTML / CSS / JS / 数据 / SVG 图标 / Canvas 粒子引擎全部内联在 `index.html` 中，约 75 KB
- **零网络请求**：不加载 Web Font、不引 CDN、不发 API；文件中唯一的 URL 是 SVG 命名空间常量 `http://www.w3.org/2000/svg`，不产生请求
- **字体**：走系统衬线栈（宋体系），跨平台无需下载
- **响应式断点**：≤1000px 双栏转单栏，≤780px 进一步压缩间距与轮盘尺寸，窄屏关闭鼠标视差
- **节气日期说明**：页面日期为通行区间（上半年 6/21、下半年 8/23 前后），未做万年历精算，交节时刻逐年略有差异
- **兼容性**：ES5 语法编写，无构建产物，现代浏览器直接可用

---

## 目录结构

```
.
├── index.html   # 全部内容（结构 + 样式 + 脚本 + 数据）
└── README.md
```

---

<a id="en"></a>

# Twenty-Four Solar Terms · The Chinese Aesthetics of Time

> A single-file educational website about the twenty-four solar terms: the solar term wheel, the seventy-two pentads, folk customs and seasonal health care, and the poetry of the terms.
> Everything lives in one `index.html` — **no build step, no dependencies, no network requests**. Just double-click to open.

![Single file](https://img.shields.io/badge/Single%20File-75%20KB-b89b6a) ![Dependencies](https://img.shields.io/badge/External%20Dependencies-0-5c8f63) ![Run](https://img.shields.io/badge/Run-Open%20in%20Browser-4d6f8f)

[中文](#zh) | **English**

---

## Page Structure

| Section | Anchor | Contents |
|---|---|---|
| Hero · Home | `#top` | Headline, lede, quick links, and the "Today's Term" card (progress ring + season switcher) |
| Solar Term Wheel | `#wheel` | A 560px SVG wheel with the 24 terms arranged radially, tinted by season, and the four cardinal points marked |
| Twenty-Four Terms | `#terms` | 24 term cards, filterable by season, with today's term flagged |
| Seventy-Two Pentads | `#hou` | 24 sets × 3 pentads, each with a plain-language gloss |
| Poetry of the Terms | `#poem` | One classical line per term, 24 in all, each with its source |
| Solar Term Song | `#song` | The complete mnemonic verse, annotated with "6th/21st in the first half of the year, 8th/23rd in the second" |

Top navigation: **Home 首页 / Pentads 七十二候 / Poetry 节气诗话 / Song 节气歌** — the current section is highlighted automatically as you scroll.

---

## Key Features

### Content

- **Today's term, computed automatically**: from the system date it derives the current term, the period it spans, the sun's ecliptic longitude, the days until the next term, and the phenology of the first pentad — landing correctly on any day of the year
- **Full dossiers for all 24 terms**: each entry carries six fields — meaning, three pentads, folk customs, health care, farm work, and a verse
- **Seventy-two pentads**: for example 「群鸟养羞 · 百鸟储食备冬」 — birds store up food against the winter
- **Poetry of the terms**: 24 celebrated lines of classical verse, each with its source

### Interaction

- **Solar term wheel**: term names run radially along the spokes (the left half is flipped 180° so it stays readable); clicking any term slides open a drawer on the right
- **Detail drawer**: close with ESC, step to the previous or next term with the ← → keys, or use the Prev / Next buttons at the bottom
- **Start tour / Back to today**: the tour advances one term every 1.6 seconds, with pointer, palette, and particles following in sync
- **Season filter**: the twenty-four terms section narrows to spring, summer, autumn, or winter
- **Season switcher**: use the "Spring / Summer / Autumn / Winter" buttons under the today card, or click any term on the wheel, and the entire site's palette migrates
- **Back to top**: a round floating button in the lower-right corner, appearing after roughly two-thirds of a screen of scrolling and gliding you smoothly back up
- **Footer email**: click to copy `imuse@163.com`

### Visuals & Motion

- **Four-season mood engine**: `body[data-season]` drives the global accent color by cross-fading four full-screen gradient layers (1.2s)

  | Spring | Summer | Autumn | Winter |
  |---|---|---|---|
  | `#5c8f63` | `#c1503f` | `#c08a2e` | `#4d6f8f` |

- **Canvas seasonal particles**: spring — blossoms spiralling down; summer — slanting rain; autumn — swinging leaves; winter — fine snow. Between 34 and 110 particles depending on screen width, DPR-aware, and paused automatically when the tab goes to the background
- **Hero background**: three large blobs of light, colored by season, drift slowly (26–38s loops); a giant 節 watermark rotates gently once every 90 seconds
- **Title shimmer**: the headline 「一轮廿四节气」 is gradient text, swept by a seasonal streak of light every 7 seconds
- **Cursor-following glow**: an accent-colored halo trails the pointer across the hero; the headline drifts slightly against it while the today card drifts with it, building depth
- **Dimensional wheel**: 13° of mouse parallax gives it depth, an outer dashed ring rotates slowly, and the current term's sector pulses continuously
- **Scroll parallax**: hero text rises at 0.22× while the light blobs and watermark fade out on exit
- **Micro-interactions**: the today card floats as if breathing, seals slowly expand and contract, buttons lift on hover, the poem card's vertical rule draws from short to full, and pentad rows shift right
- **Entrance animations**: hero layers fade in on staggered delays, grid items arrive in sequence (replayed when filtering), and the solar term song surfaces line by line

### Accessibility & Fallbacks

- All animation and particles are disabled under `prefers-reduced-motion`
- Count-up animations carry a `setTimeout` fallback, so the correct value is reached even in extreme cases
- Copying the email address degrades through three tiers: Clipboard API → 800ms timeout/failure → `execCommand` → if that fails too, the text is selected automatically with a prompt

---

## Technical Notes

- **Single file**: HTML / CSS / JS / data / SVG icons / the Canvas particle engine are all inlined in `index.html`, roughly 75 KB
- **Zero network requests**: no web fonts, no CDN, no API calls; the only URL in the file is the SVG namespace constant `http://www.w3.org/2000/svg`, which issues no request
- **Typography**: the system serif stack (Song-style faces), so nothing needs downloading on any platform
- **Responsive breakpoints**: two columns collapse to one at ≤1000px, spacing and wheel size compress further at ≤780px, and mouse parallax switches off on narrow screens
- **A note on solar term dates**: the page uses the commonly cited ranges (around the 6th/21st in the first half of the year, the 8th/23rd in the second); no perpetual-calendar precision is applied, so actual ingress times vary slightly year to year
- **Compatibility**: written in ES5 syntax with no build output, ready to run directly in modern browsers

---

## Directory Structure

```
.
├── index.html   # Everything (structure + styles + scripts + data)
└── README.md
```
