# 英雄所见 · TODO

## T1 · 划线分享卡(参照 streamer-card,2026-10-21 Kyle 提议)

**用户故事**:读者在热度榜/书序里看中一句 → 点「做成卡片」→ 前端生成精美分享卡(引文 + N 人划过 + 书名/译者 + 「英雄所见」品牌 + 二维码)→ 下载 PNG → 发朋友圈/群,扫码回流本站(#书锚点)。

**参照**:https://github.com/ygh3279799773/streamer-card(流光卡片,Puppeteer 截图 + API)。

**关键架构决策——不走 streamer-card 的服务端路线**:
- 本站是 GitHub Pages 单文件零构建,无 Node 服务;Puppeteer 方案需要常驻后端,违背家族站模式
- 改为**纯前端生成**:canvas 手绘 或 内嵌 html-to-image(~40KB 进 index.html,仍单文件零构建);复用站内既有纸墨/朱砂设计语言,不另起模板系统
- 二维码:内嵌 qrcode-generator(~10KB)离线生成,指向 `https://liyuankui.github.io/yingxiongsuojian/#lp|#jc`(带书锚点,回流即到书)

**卡片制式(对齐豆沙金句卡家族审美)**:3:4 竖版、衬线引文、朱砂热度徽章、右下浅签、底部二维码区;引文超长自动截断(卡片更短,~60 字)。

**埋点**:`card_generate{book}` / `card_download{book}`(三重闸照旧,登记进 POSTHOG_ANALYTICS.md)。

**版权**:单条引文单卡,量小;卡片水印含书名与译者署名,天然合规。

**验收**:下载 PNG 2250×3000@DPR3 级清晰度;二维码扫码直达对应书;微信内长按识别可用。

## 暂缓(明确不做)

- 版权量控制收紧(Kyle 2026-10-21 拍板:现状还好,不动)
