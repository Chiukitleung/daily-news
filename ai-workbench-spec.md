# AI 工作台 UI 设计规格（DSH 重构用）

> 来源：https://chiukitleung.github.io/daily-news/ai-workbench-ui.html （交互预览页）
> 用途：重构 AI 工作台界面时，按本规格提取设计令牌与组件规范。
> 四套主题任选其一，推荐 **Linear**（暗色工作台，最贴合开发者工具）。

---

## 主题一：Linear — 暗色工作台（推荐）

**风格**：近黑画布 + 靛紫点缀，精确工程感；信息密度靠亮度层级管理。
**适合**：项目管理台 / 任务看板 / 开发者工具 / 通用 AI 工作台暗色。

### CSS Tokens
```css
--bg:#08090a; --panel:#0f1011; --surface:#191a1b; --surface2:#28282c;
--text:#f7f8f8; --text2:#d0d6e0; --text3:#8a8f98; --text4:#62666d;
--accent:#5e6ad2; --accent2:#7170ff; --accent3:#828fff; --success:#27a644;
--border:rgba(255,255,255,.08); --border2:rgba(255,255,255,.05);
--radius:6px; --radius2:8px; --radius3:12px;
font-family:'Inter',system-ui,sans-serif; font-feature-settings:'cv01','ss03';
```

### 关键规则
1. 字形：Inter Variable，weight 400（正文）/ 510（强调，Linear 招牌）/ 590（标题），禁用 700。
2. 展示级标题负字距：48px → -1.056px；32px → -0.704px。
3. 主文本用 `#f7f8f8` 而非纯白；按钮背景用半透明白 `rgba(255,255,255,.02~.05)`。
4. 边框一律半透明白（`.05/.08`），不用实色深边框。
5. 品牌紫 `#5e6ad2 / #7170ff` 仅用于 CTA、激活态、链接。
6. 层级靠背景亮度递进（`#0f1011 → #191a1b → #28282c`），不用投影（深色上投影不可见）。
7. 圆角：按钮 6px，卡片 8px，面板 12px，胶囊 9999px。
8. 阴影用 inset 或环式（`0 0 0 1px`），投影仅用于浮层。

### 组件
- 幽灵按钮：`rgba(255,255,255,.02)` 底 + `1px solid #24282c` 边，6px 圆角
- 主按钮：`#5e6ad2` 底白字，8px 16px，hover `#828fff`
- 卡片：`rgba(255,255,255,.02)` 底 + `1px solid rgba(255,255,255,.08)` 边，8px 圆角
- 输入：`rgba(255,255,255,.02)` 底 + 半透明白边，6px 圆角；焦点 `#7170ff`
- 状态胶囊：`transparent` 底 + `1px solid #23252a` 边 + 12px/510 字重
- 成功点：`#10b981` 圆形 10px 字重 510

---

## 主题二：Vercel — 黑白极简

**风格**：纯白画布 + near-black `#171717`，Geist 字体负字距压缩；阴影代替边框。
**适合**：开发者控制台 / 数据面板 / SaaS 界面。

### CSS Tokens
```css
--bg:#ffffff; --panel:#ffffff; --surface:#fafafa; --surface2:#f5f5f5;
--text:#171717; --text2:#4d4d4d; --text3:#666666; --text4:#808080;
--accent:#171717; --accent2:#0072f5; --accent3:#0a72ef;
--border:rgba(0,0,0,.08); --border2:rgba(0,0,0,.06);
--radius:6px; --radius2:8px;
font-family:'Geist','Inter',system-ui,sans-serif; letter-spacing:-.02em;
```

### 关键规则
1. 边框一律用 shadow-as-border：`box-shadow:0 0 0 1px rgba(0,0,0,.08)`，不用 CSS border。
2. 三档字重：400（读）/ 500（交互）/ 600（标题）。
3. 工作流三色只用于流程状态：Develop `#0a72ef` / Preview `#de1d8d` / Ship `#ff5b4f`。
4. 卡片阴影栈：`0 0 0 1px rgba(0,0,0,.08), 0 2px 2px rgba(0,0,0,.04), #fafafa 0 0 0 1px`。
5. 主 CTA：黑底白字 `#171717`，6px 圆角；次要按钮白底 + 阴影边框。
6. 状态胶囊：`#ebf5ff` 底 + `#0068d6` 字，9999px 圆角。

---

## 主题三：Claude — 温暖纸感

**风格**：羊皮纸 `#f5f4ed` + 陶土色 `#c96442`，衬线标题，书刊排版。
**适合**：AI 对话产品 / 知识库 / 内容型工作台。

### CSS Tokens
```css
--bg:#f5f4ed; --panel:#faf9f5; --surface:#faf9f5; --surface2:#ffffff;
--text:#141413; --text2:#4d4c48; --text3:#5e5d59; --text4:#87867f;
--accent:#c96442; --accent2:#d97757; --accent3:#b53333; --focus:#3898ec;
--border:#f0eee6; --border2:#e8e6dc;
--radius:8px; --radius2:12px; --radius3:24px;
font-family:'Inter',system-ui,sans-serif;
```

### 关键规则
1. 全暖色调——任何灰色都要带黄棕底（`#5e5d59`、`#87867f`），禁用冷蓝灰。
2. 衬线标题（Georgia 替代）权重恒 500，无 bold。
3. 阴影用环式 `0 0 0 1px` 而非投影；需要时用极软投影 `rgba(0,0,0,.05) 0 4px 24px`。
4. 陶土色 `#c96442` 仅用于主 CTA 与品牌时刻。
5. 正文行高 1.6，书刊阅读感；无渐变。
6. 卡片 8px 圆角、banner 16-32px；按钮：暖沙 `#e8e6dc` 底 + 炭暖 `#4d4c48` 字。

---

## 主题四：Cursor — 暖色 AI 编码台

**风格**：奶油底 `#f2f1ed` + 暖近黑 `#26251e`，橙色 `#f54e00` 强调；AI 操作时间线。
**适合**：AI 编码工作台 / 展示 agent 执行过程的界面。

### CSS Tokens
```css
--bg:#f2f1ed; --panel:#f2f1ed; --surface:#e6e5e0; --surface2:#ebeae5;
--text:#26251e; --text2:rgba(38,37,30,.75); --text3:rgba(38,37,30,.55);
--accent:#f54e00; --accent2:#cf2d56; --success:#1f8a65;
--border:rgba(38,37,30,.1); --border2:rgba(38,37,30,.2);
--radius:8px; --radius2:10px;
font-family:'Inter',system-ui,sans-serif;
```

### 关键规则
1. 全暖色系，绝不出现纯白/纯黑做主面。
2. hover 时文本变绯红 `#cf2d56` 是招牌交互。
3. AI 时间线四色：thinking `#dfa88f` / grep `#9fc9a2` / read `#9fbbe0` / edit `#c0a8dd`。
4. 主按钮：暖面 `#ebeae5` 底 + `#26251e` 字，8px 圆角。
5. 投影用大模糊弥散（14-32px），营造氛围感。
6. 胶囊 9999px 用于标签筛选；次级交互 6-8px 圆角。

---

## 通用工作台布局骨架（任意主题通用）

```
┌────────────┬──────────────────────────────────────┐
│ 侧边导航    │  顶栏（搜索 / 状态 / 用户 / CTA）      │
│ · 对话工作区 │  内容区                              │
│ · 项目/任务  │    - 工作台卡片网格                  │
│ · 数据看板   │    - AI 任务时间线（如需）           │
│ · 知识库     │    - 表单/输入区                     │
│ · 设置      │                                      │
└────────────┴──────────────────────────────────────┘
```

- 侧边栏 200px，暗色主题用 `--panel`，浅色用 `--surface`；激活项左边 2px 强调条 + 背景递进。
- 内容主区 padding 20px；卡片间距 10-14px；分区间距 40px+。
- 顶栏 sticky + `backdrop-filter:blur(10px)` + 底部 1px 边框。
- 自适应：移动端侧边栏收成汉堡菜单，卡片网格 3→2→1 列。