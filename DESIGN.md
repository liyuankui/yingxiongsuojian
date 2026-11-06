# DESIGN.md · 英雄所见 — 夜航书灯世界

## Mode
Read(内容站,理解与停留)+ 卡片功能的轻 Persuade(分享即传播)。

## 世界(2026-10-21 重设计定稿)
深夜书房的灯下读书:墨蓝夜色为底,一盏暖黄书灯自顶部照下来。所有暖黄元素都是「灯光」,所有热度都是「被照见的程度」。

## Tokens
| token | 值 | 语义 |
|---|---|---|
| --night | #0c1424 | 夜(页面底) |
| --night-2 / -3 | #111d33 / #16243d | 卡面 / 抽屉 |
| --lamp | #e9c87c | 书灯(高亮/热度/当前态) |
| --lamp-deep | #c8a45a | 灯芯深(次级强调/徽章底) |
| --ink | #f0e8d8 | 灯下纸白(正文) |
| 次级文字 | rgba(240,232,216,.62/.4) | 从前景派生,非纯灰 |
| 字体 | Songti SC / Noto Serif SC | 衬线正文;Georgia italic 用于序号 |

## 已辩护的决策(与 detector warning 对质)
- **顶部 radial 书灯光晕 + 站名 text-shadow**(detect: dark-glow/radial-halo warning):保留。这是本世界的核心照明隐喻——夜航书灯,且与吉光片羽卡片的 canvas 灯晕同源(系统性而非装饰性)。饱和度已压至 .16/.35,是有目的的 lighting,不是 slop 默认。若未来调亮色调,光晕随之降级。
- 序号 Georgia italic:灯下刻度的年代感。
- 无 kicker/eyebrow(craft-floor 硬禁):站名直接开口。
- 对比度:正文 #f0e8d8 on #0c1424 ≈ 13:1;次级 .62 ≈ 8:1;faint .4 仅用于页脚/章名辅助(非正文),大号场景。

## 吉光片羽(卡片)
canvas 750×1000 本地生成:夜底+顶部灯晕+「英雄所见」+书名副题+衬线引文(≤7 行自动换行,超 126 字截断)+暖黄热度行+书名译者章+右下二维码(内嵌 qrcode-generator,指回 #book 锚点)。触发:列表条目「羽」按钮 → 底部抽屉。埋点 card_generate/card_download。

## 版式纪律
- line-break: strict;行首禁则
- 移动端优先(720px 容器,clamp 标题,书架横滚)
- hash 路由 + hashchange(家族深链三必须)
