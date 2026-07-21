
# Japanese Electric Utility Cost and Generation Data

日本の電力会社が有価証券報告書等で開示している発電種別の原価明細および発電実績を、会社間・年度間で比較できるように正規化したデータセットです。

This repository contains normalized cost breakdown and electricity generation data disclosed by Japanese electric utility companies.

## Datasets

- `data/electric_utility_costs_normalized.csv`
  - 電気事業営業費用・原価明細
  - Electric utility operating and cost breakdown data

- `data/electricity_generation_by_source_normalized.csv`
  - 電源別発電実績
  - Electricity generation by energy source

## Important Notes

- 合計項目とその内訳項目が含まれるため、全行を単純合計すると二重計上になる場合があります。
- 空欄はゼロを意味しません。
- 会社・年度によって開示範囲や勘定科目の定義が異なる場合があります。

The dataset may contain both account totals and their detailed components. Summing all rows may result in double counting. Blank values should not be interpreted as zero.

For details, see [METHODOLOGY.md](METHODOLOGY.md).

## Source

Publicly available annual securities reports through Japan's EDINET system.

## Website


https://dig-the-company.com/
