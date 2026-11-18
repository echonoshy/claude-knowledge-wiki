# 本地建库与核对记录

输入为默认 `core` 8 份公开 SEC 文件，加模拟 Word、模拟 CSV、真实董事会演示稿前 6 页，共 11 份资料。公开原件通过 HTTP 获取。提取与核对在本地利用文本和 PDF 图像完成，采用 Markdown 与 YAML 格式。

## 流程

1. **取资料并转换。** 解析 SEC 主申报文件 HTML，读取 Word 的段落与表格，以及 CSV 的字段与记录。扫描演示稿逐页渲染并用本地 OCR 转录，对照六张图确认写入 Wiki 的图表数字。保留原文件链接与页码。
2. **分批和提取。** 复用教程的纯 Python 分批算法，每批约 12 万字符。原始资料分成 25 批，全批次扫描主题线索。归档的内容为围绕示例交易有出处的摘录、关系和数值。源文件、章节表格和 PDF 的范围见下方。
3. **补查。** 处理 10 个优先问题。解决 7 个，确认 3 个在本语料内无法回答，另记录 8 个待补问题。
4. **核对。** 回查来源行号与页码，复算 EBITDA 调节、股份回购均价和融资加总，区分原方案、修订、交割与预测数据。比对交易对方的直接持股、基金层级和别名。
5. **整理。** 将登记结果写成 56 条逐来源事实、32 条关系、65 条指标。合并可确认的实体别名，保留不同财务口径并按优先级整理 8 项疑点。核查索引、链接和来源定位。

批次主题扫描用于定位原文，Wiki 收录的是核过来源的关键事实。原始申报文件的完整内容可从来源页查阅。

## 补查结果

- **Q-01 · RESOLVED** 最终合并对价多少？旧的 44.00 美元怎么处理？ [见该资料的问题记录](open_questions/8k-closing.md)
- **Q-02 · RESOLVED** 为什么资料里会同时出现 21 亿和 23 亿美元的贷款？ [见该资料的问题记录](open_questions/8k-closing.md)
- **Q-03 · CONFIRMED UNRESOLVABLE** 2025 财年实际营收是多少？ [见该资料的问题记录](open_questions/board-deck-cii.md)
- **Q-04 · RESOLVED** 2023 财年 235.404 百万和约 252 百万美元的 EBITDA 能否合并？ [见该资料的问题记录](open_questions/analyst-note.md)
- **Q-05 · RESOLVED** Topco 是不是 Parent 的直接股东，实际谁并入目标公司？ [见该资料的问题记录](open_questions/defm14a-merger-proxy.md)
- **Q-06 · RESOLVED** Accel 六只基金的合计为什么比关联方一栏少 49,190 股？ [见该资料的问题记录](open_questions/def14a-2024.md)
- **Q-07 · RESOLVED** GA 在底层登记持有多少股？ [见该资料的问题记录](open_questions/defm14a-merger-proxy.md)
- **Q-08 · CONFIRMED UNRESOLVABLE** 为何 22.17 美元回购均价与现金除股数算出的约 20.32 美元不同？ [见该资料的问题记录](open_questions/10k-fy2023.md)
- **Q-09 · RESOLVED** 两家顾问的约 4,500 万美元属于同一笔费用吗？ [见该资料的问题记录](open_questions/defm14a-merger-proxy.md)
- **Q-10 · CONFIRMED UNRESOLVABLE** 交割时两只发起方最终签署及实际出资金额是多少？ [见该资料的问题记录](open_questions/8k-amended-agreement.md)
- **Q-11 · OPEN** 原 8-K 的赔偿上限摘要怎样与附件 A §8.3 救济逻辑逐个触发条件对齐？ [见该资料的问题记录](open_questions/8k-merger-announcement.md)
- **Q-12 · OPEN** 修订协议涉及的赔偿上限和例外如何在签署附件中定义？ [见该资料的问题记录](open_questions/8k-amended-agreement.md)
- **Q-13 · OPEN** 对于 9 月改为 46.50 美元的结构，有无后续公平性意见？ [见该资料的问题记录](open_questions/board-deck-cii.md)
- **Q-14 · OPEN** 虚构笔记所用的信贷协议 EBITDA 口径可否逐项重算？ [见该资料的问题记录](open_questions/analyst-note.md)
- **Q-15 · OPEN** 交割定期贷款为什么比 8 月承诺少 2 亿美元，另外两档在交割日提款多少？ [见该资料的问题记录](open_questions/8k-closing.md)
- **Q-16 · OPEN** 商誉减值的估值敏感性可以推算到什么程度？ [见该资料的问题记录](open_questions/10k-fy2022.md)
- **Q-17 · OPEN** 一季度之后的全年实际走势如何？ [见该资料的问题记录](open_questions/10q-q1-2024.md)
- **Q-18 · OPEN** 模拟供应商的 1,750 人代表什么统计口径？ [见该资料的问题记录](open_questions/data-provider-extract-csv.md)

## 输入及核对清单

| 来源 | 文本字符 | 行数 | SHA-256（规范化文本） |
| --- | ---: | ---: | --- |
| [2022 财年 Form 10-K 年报](entities/10k-fy2022.md) | 450,745 | 2,683 | `1f504da1b127f67cd594461a8a75373ae1b9672de10bb90ca4b02f9c3aa309f3` |
| [2023 财年 Form 10-K 年报](entities/10k-fy2023.md) | 471,440 | 2,787 | `4591eb78c77c8ef58aa062fc99be59103fcf84b869063e04834c076d26366f2b` |
| [2024 年年度股东大会 DEF 14A 委托书](entities/def14a-2024.md) | 155,618 | 1,081 | `a6ad1573a0f86af4683584fa8aa8bb97675ffa60a0d1c7b5e437cdace9be587d` |
| [2024 年第一季度 Form 10-Q](entities/10q-q1-2024.md) | 293,354 | 1,622 | `daf94ed6cedea2abc87410eef6f37d36bb56aa2da05068c553257646fc81a58b` |
| [2024-05-13 原始合并协议 Form 8-K](entities/8k-merger-announcement.md) | 32,029 | 119 | `ba81870afe882aefd38e9ee38da1f40ff0f4b3766a40d752fc600cf0af874fe6` |
| [2024-08-22 合并 DEFM14A 委托书](entities/defm14a-merger-proxy.md) | 1,298,954 | 8,466 | `651c05e91a77f9662541cb48dccaebe45748ab27ddd2ecfa900e9482481d0b1e` |
| [2024-09-09 修订协议 Form 8-K](entities/8k-amended-agreement.md) | 34,872 | 259 | `5cfcd4ef66a72efc262856e57276b0bc9f738826549b8e74a6a2bd61638f9ac9` |
| [2024-10-17 交割 Form 8-K](entities/8k-closing.md) | 18,031 | 175 | `1aadc4df1e5abf33ad08a90bd9605045ef99d2f3ae43cc9bcd3a9602c3664c1b` |
| [Centerview 董事会特别委员会讨论材料（前 6 页）](entities/board-deck-cii.md) | 12,766 | 458 | `7bc1274a0a5f52ca6190b57087583370a8d7161d80a8e2fcdad13e328ca2a9ff` |
| [模拟 Word 分析笔记](entities/analyst-note.md) | 1,217 | 17 | `3f54d046006f6249f0395b49d2363150365b8b3c1391757dc02ac6f2cb66f97a` |
| [模拟供应商 CSV](entities/data-provider-extract-csv.md) | 855 | 8 | `63b35fcd188a9c9800660d7b7e67ea8250af46cab293fd2a6bfc6a1fb1200741` |

## 分批扫描清单

主题命中数用于定位材料，命中可以重叠，也可能是标题或同一事实的重复出现。

| 批 | 文档或分片 | 字符 | 治理 | 交易 | 财务 | 来源与限制 |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| batch-01 | `10k_fy2022.part1.txt` | 120,194 | 6 | 2 | 62 | 31 |
| batch-02 | `10k_fy2022.part2.txt` | 120,194 | 67 | 0 | 131 | 13 |
| batch-03 | `10k_fy2022.part3.txt` | 120,194 | 30 | 0 | 208 | 37 |
| batch-04 | `10k_fy2022.part4.txt` | 90,761 | 45 | 9 | 52 | 6 |
| batch-05 | `10k_fy2023.part1.txt` | 120,194 | 6 | 2 | 59 | 30 |
| batch-06 | `10k_fy2023.part2.txt` | 120,194 | 62 | 0 | 120 | 10 |
| batch-07 | `10k_fy2023.part3.txt` | 120,194 | 22 | 0 | 222 | 44 |
| batch-08 | `10k_fy2023.part4.txt` | 111,456 | 49 | 9 | 129 | 11 |
| batch-09 | `10q_q1_2024.part1.txt` | 120,194 | 20 | 2 | 244 | 86 |
| batch-10 | `10q_q1_2024.part2.txt` | 120,194 | 4 | 0 | 101 | 21 |
| batch-11 | `10q_q1_2024.part3.txt` | 53,370 | 56 | 6 | 41 | 4 |
| batch-12 | `def14a_2024.part1.txt` | 120,197 | 189 | 1 | 21 | 6 |
| batch-13 | `def14a_2024.part2.txt` | 35,634 | 78 | 0 | 10 | 1 |
| batch-14 | `defm14a_merger_proxy.part1.txt` | 120,205 | 157 | 172 | 24 | 7 |
| batch-15 | `defm14a_merger_proxy.part2.txt` | 120,205 | 76 | 110 | 10 | 4 |
| batch-16 | `defm14a_merger_proxy.part3.txt` | 120,205 | 80 | 186 | 31 | 37 |
| batch-17 | `defm14a_merger_proxy.part4.txt` | 120,205 | 79 | 80 | 85 | 81 |
| batch-18 | `defm14a_merger_proxy.part5.txt` | 120,205 | 75 | 215 | 35 | 4 |
| batch-19 | `defm14a_merger_proxy.part6.txt` | 120,205 | 140 | 54 | 18 | 4 |
| batch-20 | `defm14a_merger_proxy.part7.txt` | 120,205 | 57 | 13 | 39 | 5 |
| batch-21 | `defm14a_merger_proxy.part8.txt` | 120,205 | 29 | 4 | 30 | 3 |
| batch-22 | `defm14a_merger_proxy.part9.txt` | 120,205 | 67 | 19 | 76 | 0 |
| batch-23 | `defm14a_merger_proxy.part10.txt` | 120,206 | 288 | 71 | 12 | 2 |
| batch-24 | `defm14a_merger_proxy.part11.txt` | 98,972 | 176 | 58 | 11 | 0 |
| batch-25 | `8k_amended_agreement.txt`、`8k_closing.txt`、`8k_merger_announcement.txt`、`analyst_note.txt`、`board_deck_cii.txt`、`data_provider_extract.csv.txt` | 99,770 | 44 | 173 | 35 | 47 |
