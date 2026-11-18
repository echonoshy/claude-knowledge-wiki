---
name: data-provider-extract-csv
description: "SYNTHETIC。模拟 CSV"
aliases: []
metadata:
  type: event
---

# 模拟供应商 CSV


## 来源

- SYNTHETIC。模拟 CSV。基准日期为 undated。 [查看原件](../../example_data/data_provider_extract.csv)
- 本地规范化文本位于 `data_room/docs/data_provider_extract.csv.txt`。行号包含来源标记与空行。
- [逐来源指标](../metrics/data-provider-extract-csv.md) · [关系](../relations/data-provider-extract-csv.md) · [问题](../open_questions/data-provider-extract-csv.md)

## 事实

- AlphaData 与 BetaFeed 记录使用不同名称、代码形式和四舍五入精度，但均指 Squarespace, Inc. 演示行不作官方财务证据。 [source: [data-provider-extract-csv](../entities/data-provider-extract-csv.md) | as-of: undated | 规范化文本第 4–5 行]
- Spaceship Purchaser 是单列实体。Block（旧称 Square）和虚构的 Squarespace Technologies Ltd 是同名近似项，不与 Squarespace 合并。 [source: [data-provider-extract-csv](../entities/data-provider-extract-csv.md) | as-of: undated | 规范化文本第 6–8 行]
