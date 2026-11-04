# PostHog 事件字典 · yingxiongsuojian

project 值:`yingxiongsuojian`(查询永远带 `properties.project = "yingxiongsuojian"` 过滤)
uid:家族共享 `sbf-uid`(与饮水思源/入乡随俗等同 origin 合并 Person)
三重闸:file:// 预览 / webdriver 自动化 / localhost 本地服务一律不报

| 事件 | 属性 | 触发 |
|---|---|---|
| `page_view` | book: lp/jc | 首次加载 |
| `book_view` | book: lp/jc | 点书切换 |
| `tab_view` | book, tab: hot/seq/x | 切 tab(译本对照=x 是本站特色,重点观测) |
| `share_click` | book | 点分享按钮 |

诚实度量口径:活跃用户用 `countDistinctIf(distinct_id, event != 'page_view')`;自查排除自己的 id(控制台 `localStorage.getItem('sbf-uid')`)。
