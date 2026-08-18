# Board Game Designer 实战案例：敦煌·九色鹿

> 用 Board Game Designer 设计一个真正的 9 卡游戏（nanogame）。

## 什么是 9 卡游戏

9 卡游戏（9-card nanogame）是 BGG 上的经典微桌游设计挑战：

- **整个游戏只有 9 张卡**——没有版图、没有 token、没有骰子
- **每张卡身兼多职**——同一张卡在不同情境下有不同用途
- **完整的游戏体验**——有策略深度，不只是玩具
- **PnP 友好**——打印 9 张卡就能玩

代表作：Agent Decker（间谍主题单人游戏）、Maquis（法国抵抗运动单人游戏）

---

## 设计者输入

```
我想做一个敦煌主题的9卡游戏，给朋友聚会用，轻松一点的。
```

---

## Phase 0 · 诊断

### Board Game Designer 提问

```
好的，敦煌主题 + 9卡格式，很有挑战性。

9卡游戏的核心约束是：整个游戏只有9张卡，每张卡要身兼多职。
没有额外的 token、骰子或版图。

在深入之前，我想确认几个关键点：

1. 两个人玩还是可以更多？
2. 你希望每张卡有多少种用途？（越多越复杂但越有深度）
3. 你玩过什么 9 卡或微桌游游戏吗？（帮我了解你的经验水平）
```

### 设计者回答

```
两个人玩。每张卡2-3种用途吧。没玩过9卡游戏，但玩过璀璨宝石。
```

### Board Game Designer 搜索

自动搜索了：
- "9 card nanogame BGG" → 发现这是 BGG 经典设计挑战，代表作 Agent Decker、Maquis
- "9卡游戏设计技巧" → 关键原则：多用途卡牌、规则极简、每张卡都是关键决策
- "敦煌 桌游" → 市面极少，蓝海主题

---

## Phase 1 · 方向诊断

### Board Game Designer 输出

```
基于 9 卡格式的约束，我给你 2 个方向：

### 方向A: 多用途收集 · 每卡三种用法

**核心体验**：每张卡可以打出得分、弃掉触发效果、或保留在手牌中
            作为终局计分条件。
**参考经典**：Agent Decker（多用途卡牌）+ 璀璨宝石（收集感）
**机制**：多用途卡 + 成套收集
**每张卡的三种用途**：
  ① 打出到自己的「收藏」→ 得分
  ② 弃掉触发一次性效果 → 干扰对手/整理手牌
  ③ 保留在手牌 → 终局满足条件加分
**优势**：每张卡都是"留还是用"的痛苦抉择
**风险**：三种用途可能让新手困惑
**时长**：约 10-15 分钟

### 方向B: 双面卡 · 翻面切换身份

**核心体验**：每张卡正反两面不同——正面是壁画碎片（得分），
            反面是守护神（能力）。你只能看到自己手牌的一面。
**参考经典**：Coup（隐藏身份）+ Maquis（资源管理）
**机制**：隐藏信息 + 区域控制（轻量）
**优势**：信息不对称创造"读人"乐趣
**风险**：需要设计正反两面内容，工作量翻倍
**时长**：约 10 分钟

你更倾向哪个？方向 A 更有策略深度，方向 B 更有社交互动。
```

### 设计者选择

```
方向A，三种用途听起来很有意思。
```

### Board Game Designer 回应

```
好，方向A确认：多用途收集，每张卡三种用法。

核心机制：
- 每张卡有 基础分值 + 一次性效果 + 收藏倍率
- 打出到收藏 → 获得基础分 × 收藏倍率
- 弃掉 → 触发一次性效果（干扰/整理/查看）
- 保留在手牌 → 不得分但增加手牌上限

进机制设计？
```

### 设计者确认

```
进。
```

---

## Phase 2 · 机制设计

### Board Game Designer 输出

```
### 机制组合

**核心机制：多用途卡 (Multi-Use Cards)**
  → 每张卡有三种使用方式，打出/弃掉/保留
  → 经典案例：Agent Decker、Sprawlopolis
  → 这个游戏里：每张卡 = 壁画碎片（得分）+ 法术（效果）+ 手牌资源

**辅助机制：成套收集 (Set Collection)**
  → 收集同类型壁画得倍率奖励
  → 经典案例：璀璨宝石、Jaipur

**辅助机制：手牌管理 (Hand Management)**
  → 每回合摸1张打1张，手牌上限3张
  → 什么时候用效果、什么时候留着得分，是核心抉择

**回合结构：固定顺序，每回合摸1张+执行1个行动**

**结束条件：牌堆耗尽 + 某玩家手牌为空**

### 分值设计

| 卡牌类型 | 基础分 | 收藏倍率 | 数量 |
|---------|--------|---------|------|
| 普通壁画 | 1分 | ×1 | 3张 |
| 稀有壁画 | 3分 | ×2 | 3张 |
| 传说壁画 | 5分 | ×3 | 3张 |

**分数计算**：基础分 × 同类型收藏数量 × 倍率

示例：
- 收藏 2 张普通：1×2×1 = 2分
- 收藏 3 张稀有：3×3×2 = 18分
- 收藏 1 张传说：5×1×3 = 15分
```

### Board Game Designer 提问

```
几个确认：

1. 效果是"弃掉触发"还是"打出触发"？
   → 我建议：弃掉触发（这样打出=得分，弃掉=效果，选择更清晰）

2. 倍率系统会不会太复杂？（基础分 × 数量 × 倍率）
   → 简化方案：去掉倍率，直接基础分 × 数量

3. 传说卡的效果应该很强（弃掉代价大），你接受吗？
```

### 设计者回答

```
弃掉触发。倍率保留，让传说卡更有价值。传说卡效果强OK。
```

---

## Phase 3 · 组件设计

### Board Game Designer 输出

```
### 组件清单

**9 张卡牌（无其他组件）**

每张卡包含：
- 上部：壁画名称 + 类型图标（普通/稀有/传说）
- 中部：壁画插画描述
- 下部：基础分值 + 弃掉效果描述

| # | 名称 | 类型 | 基础分 | 弃掉效果 |
|---|------|------|--------|---------|
| 01 | 卷草纹 | 普通 | 1 | 摸 2 张牌，弃回 1 张 |
| 02 | 莲花纹 | 普通 | 1 | 将手牌中 1 张放到牌堆顶 |
| 03 | 忍冬纹 | 普通 | 1 | 查看牌堆顶 2 张，放回任意顺序 |
| 04 | 飞天 | 稀有 | 3 | 偷看对手 1 张手牌 |
| 05 | 莲花童子 | 稀有 | 3 | 与对手各盲换 1 张手牌 |
| 06 | 供养人 | 稀有 | 3 | 从牌堆中搜索 1 张牌加入手牌，洗牌 |
| 07 | 佛像 | 传说 | 5 | 从对手收藏中偷 1 张到自己收藏 |
| 08 | 九色鹿 | 传说 | 5 | 对手必须给你 1 张手牌（你选） |
| 09 | 莫高窟 | 传说 | 5 | 对手下回合跳过（你连续行动 2 次） |
```

### Board Game Designer 提问

```
效果复杂度检查——普通卡效果简单（摸牌/排序），传说卡效果强（偷牌/抢回合）。
你觉得这个梯度合理吗？有没有哪张卡的效果你觉得太强或太弱？
```

### 设计者回答

```
看起来不错。佛像偷收藏的卡会不会太强？
```

### Board Game Designer 回应

```
佛像确实是最强效果，但代价也大——弃掉一张 5 分的传说卡。
弃掉它 = 损失 15 分潜在得分（5×3），换来偷对手 1 张收藏。

如果对手收藏了 3 张稀有（18分），你偷 1 张 = 对手-6分 你+6分，
净差 12 分，但你损失了 15 分。所以不一定赚。

平衡的关键在于时机——后期偷高分收藏才值得。

你觉得这个平衡OK吗？
```

### 设计者确认

```
OK，逻辑说得通。继续。
```

---

## Phase 4 · 数值平衡

### Board Game Designer 输出

```
### 数值平衡报告

**游戏时长**：
  - 9 张卡 / 2 人 = 每人约 4-5 张手牌总量
  - 每回合摸 1 打 1 = 约 4-5 回合/人
  - 每回合约 1-2 分钟（思考 + 执行）
  - 总时长：约 8-15 分钟 ✅

**理论最高分（一人独占所有卡）**：
  - 3 普通 × 1 × 1 = 3 分
  - 3 稀有 × 3 × 2 = 18 分
  - 3 传说 × 5 × 3 = 45 分
  - 总计：66 分（不可能，但说明传说卡是核心争夺点）

**实际预期得分分布**：
  - 每人约 4-5 张卡
  - 典型得分：20-40 分
  - 分差通常在 5-15 分之间

**平衡性检查**：
  - ✅ 先手优势：轻微（先摸牌），但手牌限制削弱了先手优势
  - ✅ 雪球效应：传说卡弃掉效果可以逆转，防止一家独大
  - ✅ 国王制造：不存在（2人游戏，每个人都在为自己）
  - ✅ 信息对称：双方都能看到对手的收藏，决策有依据
  - ⚠️ 佛像 + 九色鹿组合：如果一人同时拿到两张传说，可能过于强大
    → 建议：传说卡的效果设计为互斥——佛像偷收藏，九色鹿抢手牌，
      两者不能同时对同一目标使用

**运气/策略比**：
  - 摸牌顺序 = 运气（约 30%）
  - 何时用效果 vs 何时留着得分 = 策略（约 70%）
```

### 设计者确认

```
数值OK。进规则书。
```

---

## Phase 5 · 规则书

### Board Game Designer 输出

完整的规则书见同目录下的 `rules.md`。

### 设计者确认

```
规则读了一遍，没什么问题。可以做美术了。
```

---

## 🚧 硬门槛

设计者明确说"可以做美术了"，解锁 Phase 6。

---

## Phase 6 · 美术提示词

### 设计者选择工具

```
用 ChatGPT 生成。
```

### 设计者提供参考图

上传了一张敦煌壁画的图片。

### Board Game Designer 分析参考图

```
我看了你的参考图，提取以下风格要素：

- 配色：土黄/赭石为主色，石青/石绿点缀，金色高光
- 画风：工笔重彩，线条流畅细腻
- 材质感：岩壁/矿物颜料质感
- 氛围：庄严、古朴、神圣
```

### 美术提示词输出

#### 9 张卡牌通用风格

```
Card illustration in Dunhuang Mogao Caves mural style.
Color palette: ochre yellow and sienna brown primary,
mineral blue and mineral green accents, gold highlights.
Style: meticulous Chinese gongbi painting, flowing lines,
mineral pigment texture. Border: ornate scroll pattern frame.
Mood: solemn, ancient, sacred. Poker card format.
```

#### 卡牌 01-03（普通壁画）

```
Card 01 - 卷草纹 (Scroll Grass Pattern):
Dunhuang decorative scroll pattern, symmetrical intertwining
vines and leaves. Ochre and mineral green on dark background.
Ancient wall painting texture. Clean, elegant botanical motif.

Card 02 - 莲花纹 (Lotus Pattern):
Sacred lotus flower in full bloom, viewed from above.
Dunhuang mural style, symmetrical. Mineral blue petals,
gold pistil. Ochre background with rock texture. Serene.

Card 03 - 忍冬纹 (Honeysuckle Pattern):
Classic Dunhuang honeysuckle scroll motif. Flowing curves
with pointed leaf tips. Mineral green and gold on ochre.
Geometric-meets-organic decorative design.
```

#### 卡牌 04-06（稀有壁画）

```
Card 04 - 飞天 (Flying Apsara):
Dunhuang flying celestial gracefully soaring through clouds.
Flowing ribbons and scarves trailing. Gongbi style, mineral
pigments. Ochre, sky blue, gold palette. Ethereal, divine.

Card 05 - 莲花童子 (Lotus Child):
Cherubic child on open lotus flower, Dunhuang mural style.
Round face, gentle smile, flowing fabric. Pink lotus,
green leaves, gold ornaments. Warm, innocent.

Card 06 - 供养人 (Donor/Patron):
Noble donor in Tang dynasty dress, devotional pose.
Rich robes with intricate patterns, elaborate headdress.
Deep red robe, gold trim. Dignified, pious.
```

#### 卡牌 07-09（传说壁画）

```
Card 07 - 佛像 (Buddha):
Seated Buddha in meditation, Dunhuang cave sculpture style.
Golden skin, blue hair spiral, red and gold robes.
Halo with flame pattern. Majestic, serene, sacred.

Card 08 - 九色鹿 (Nine-Color Deer):
Mythical nine-color deer from Dunhuang Jataka tale.
Luminous white body, rainbow mane and antlers.
Standing by river, graceful. Enchanted, noble.

Card 09 - 莫高窟 (Mogao Caves):
Mogao Caves cliff face with multiple cave entrances.
Golden ochre cliff, glowing interiors. Flying apsaras
floating around. Silk road landscape. Grand, awe-inspiring.
```

---

## 完成

设计者拿到以上所有内容后：
1. 用 ChatGPT 生成 9 张卡牌插画
2. 排版成扑克牌尺寸，打印
3. 找朋友测试
4. 根据测试反馈回到对应 Phase 迭代

**从想法到可测试原型，全程约 1 小时对话。**
