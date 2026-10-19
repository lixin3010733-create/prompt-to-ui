# 03 · 提示词模板

模板的设计原则：**把三层都写死，只让模型决定它该决定的事**。

## 通用模板

```
# 1 · Components —— 组件层（不许自由发挥）
Use component geometry from [Ant Design / TDesign / Shadcn UI].
Do not introduce any component style outside this library.

# 2 · Screens —— 要生成哪几屏，每屏含什么
Generate 3 mobile screens for a(n) [行业] app:

1) Onboarding
   Full-bleed hero image, headline, supporting line,
   pagination dots, primary + secondary CTA, skip affordance

2) Home
   Greeting row with avatar, search field, category chips,
   section header, [n] list rows with thumbnail + meta + tags,
   bottom tab bar

3) Detail
   Hero image with floating back / share, floating date badge,
   title block, [n] statistic cards, participant avatars,
   itinerary timeline, sticky bottom CTA bar with price

# 3 · Imagery —— 图库层
Use Unsplash photography matched to these keywords:
[keyword 1], [keyword 2], [keyword 3], [keyword 4].
Keep the visual register consistent.
Do not use close-up faces.

# 4 · Copy —— 大模型层
UI copy in [English / Chinese].
Names, distances, durations, prices and ratings are placeholder data
and must stay internally consistent
(e.g. distance and duration must match, difficulty tag must match elevation).

# 5 · Constraints —— 设计 token
Radius scale 6 / 10 / 14 / 20. Spacing on an 8pt grid.
Control height 44-50px. Max three levels of information hierarchy.
Palette: [深色] #XXXXXX / #XXXXXX, accent #XXXXXX, background #XXXXXX.
No pure black, no pure white.
```

## 五个填槽的位置

| 槽位 | 填什么 | 填错的后果 |
|---|---|---|
| `[组件库]` | Ant Design / TDesign / Shadcn UI | 空着 = 模型自由发挥控件样式 |
| `[行业]` + 每屏清单 | 具体页面名与区块 | 只写「做一个 App」= 得到通用首页 |
| `[keywords]` | 3–5 个题材词 + 禁止项 | 太宽泛 = 图片风格打架 |
| `[语言]` | English / Chinese | 混写 = 中英夹杂 |
| `[色板]` | 具体十六进制值 | 只写「森林绿」= 每次色值不同 |

## 三个可直接用的变体

### 变体 A · 深色金融看板

```
Components: Ant Design
Screens: dashboard · asset detail · add transaction
Imagery: none — use data visualisation instead of photography
Copy: English, numbers internally consistent (holdings sum to total)
Constraints: radius 6/8/12, dense 4pt sub-grid, dark #0F1712 surfaces,
             accent #4ADE80, semantic red/green must carry a second cue beyond colour
```

改了什么：图库层关掉，改成数据可视化；强调色换成语义色；补了一条无障碍要求。

### 变体 B · 浅色电商

```
Components: TDesign
Screens: splash · product list · product detail
Imagery: Unsplash, keywords: minimal product photography, soft daylight, muted background
Copy: Chinese, prices in CNY, discounts and original prices must be consistent
Constraints: radius 8/12/16, paper #F7F5F0 surfaces, accent #C8452F,
             price is the strongest element on any card
```

改了什么：图源从风景换成静物摄影；占位数据加了货币单位与一致性要求；明确了视觉重心。

### 变体 C · 后台管理系统

```
Components: Ant Design
Screens: login · data table · settings
Imagery: none, except empty-state illustration
Copy: Chinese, table rows must include edge cases — long text, empty cell, overflow tag
Constraints: radius 6/8, dense layout, control height 32px (compact mode),
             include empty / loading / error states for every list
```

改了什么：特意要求异常状态 —— 这是 AI 生成界面的最大盲区。

## 迭代提示词

第一版不满意时，不要重来，用局部指令改：

- `Keep the layout, change the palette to a warmer one.`
- `The home screen is too dense — remove the section header and keep three rows.`
- `All images should be golden hour, not midday.`
- `Rewrite every headline in under 6 words.`
- `Add empty, loading and error states to the list.`

局部指令的成本远低于重新生成，也更可控。

上一篇：[02 · 工具横向对比](02-tool-comparison.md) · 下一篇：[04 · 避坑清单](04-pitfalls.md)
