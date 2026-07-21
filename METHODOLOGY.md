# Methodology
（205行目より日本語で記載しています）

## 1. Dataset Overview

This dataset organizes and normalizes cost and expense breakdowns disclosed by Japanese electric utility companies in their annual securities reports, enabling comparisons across companies and fiscal years.

The dataset primarily includes the following electric utility-related expense items:

* Fuel costs
* Purchased power costs
* Personnel expenses
* Repair and maintenance expenses
* Depreciation
* Water usage fees
* Outsourcing expenses
* Rental expenses
* Nuclear power facility decommissioning expenses
* Other electric utility operating expenses
* Detailed components of individual expense categories

Account names and descriptions that differ across companies have been standardized where reasonably possible to facilitate cross-company analysis.

## 2. Data Sources

The data is derived from the Detailed Schedules of Electric Utility Operating Expenses included in the annual securities reports published by each company.

The original source documents are company filings made available through EDINET, the electronic disclosure system operated by Japan’s Financial Services Agency.

This dataset is not an official dataset published by the electric utility companies. It was independently created from publicly available disclosure documents.

## 3. Data Extraction Method

Numerical values were extracted from tables included in annual securities reports.

The meaning of each value was determined using information such as:

* The hierarchical structure of headings in the document
* Row labels
* Column labels
* Reporting periods
* Units
* Hierarchical relationships within each table

The extraction and classification processes are rule-based and deterministic.

Generative AI was not used to estimate, generate, or fill in numerical values.

## 4. Reporting Period

Each fiscal year is generally based on the fiscal year-end of the relevant company.

For most Japanese electric utility companies, the applicable fiscal year ends on March 31.

Quarterly and interim figures are generally excluded, and only full-year figures are included.

However, fiscal year-ends and reporting periods may differ among companies. Users should confirm the reporting period of each record when conducting year-to-year comparisons.

## 5. Consolidated and Non-consolidated Data

The figures in this dataset are presented on a non-consolidated, parent-company basis.

## 6. Account Normalization

In the original disclosures, companies may use different account names for expenses of a similar nature.

Examples include:

* Fuel costs
* Fuel costs for steam power generation
* Thermal power fuel costs
* Raw material costs
* Fuel and purchased power costs

To enable cross-company comparisons, the original labels were reviewed and mapped to common standardized categories.

Examples of standardized categories include:

* Fuel costs
* Purchased power costs
* Personnel expenses
* Repair and maintenance
* Depreciation
* Water usage fees
* Outsourcing expenses
* Rental expenses
* Nuclear-related expenses
* Other operating expenses

The standardized category names do not necessarily correspond exactly to the account names used in the original disclosures.

Where a column containing the original account name is available, users should review it together with the standardized category.

## 7. Treatment of Detailed Breakdown Items

This dataset may include not only the total value of an expense account but also its detailed components.

For example, welfare expenses may be broken down into:

* Statutory welfare expenses
* General welfare expenses

Detailed breakdown items are components of their parent expense accounts.

Therefore, simply adding both the parent account and its detailed components may result in double counting the same expense.

Depending on the purpose of the analysis, users should select one of the following approaches:

* Use only total expense account values
* Use only detailed breakdown items
* Aggregate the values after confirming their parent-child relationships

### Important Notice

The category column may contain both total expense accounts and their detailed components.

Simply summing all rows in the dataset will not produce the company’s total costs or total operating expenses.

## 8. Missing Values and Zero

A blank value does not necessarily mean zero.

Blank values may occur for the following reasons:

* The relevant item was not disclosed
* No corresponding expense existed during the fiscal year
* The amount was included in another expense account
* The value could not be reliably identified from the original disclosure
* The disclosure classification changed
* Comparable data was unavailable

As a general rule, a value of `0` is entered only when zero was explicitly disclosed or when the original table clearly indicated that the amount was zero.

Replacing blank values with zero may result in an understatement of expenses.

## 9. Considerations for Cross-company Comparisons

Electric utility companies differ in their power generation mix and business structures.

Relevant differences may include:

* The mix of hydroelectric, thermal, nuclear, and renewable power generation
* The proportion of internally generated electricity and purchased electricity
* The separation of power transmission and distribution businesses
* The consolidation scope of power generation companies and fuel procurement companies
* The treatment of jointly owned companies such as JERA
* The existence of businesses other than electric utility operations
* The decommissioning status of nuclear power plants

For this reason, users are encouraged to analyze the cost data together with generation volumes, electricity sales volumes, and the power generation mix, rather than relying solely on simple monetary comparisons.

## 10. Data Validation

The data is primarily validated using the following methods:

* Comparison with totals shown in the original disclosures
* Comparison of the sum of detailed components with the corresponding expense account total
* Duplicate checks for the same company, fiscal year, and category
* Verification of units and reporting periods
* Consistency checks across adjacent fiscal years
* Review of mappings between original account names and standardized categories
* Identification of material changes and outliers
* Manual review of significant discrepancies

However, complete accuracy cannot be guaranteed for every record.

## 11. Dataset Limitations

This dataset is subject to the following limitations:

* Disclosure formats differ among companies.
* Table structures may change from year to year, even for the same company.
* Standardized categories were independently defined for analytical purposes.
* Some items may reasonably be classified into more than one category.
* Only part of an expense account breakdown may be disclosed in the original document.
* The aggregation scope of total values and detailed breakdown values may not always be identical.
* Segment reorganizations and corporate separations may reduce year-to-year comparability.
* Normalization may remove certain detailed accounting distinctions contained in the original labels.

Users should always refer to the original company disclosures when making important decisions.

## 12. Updates and Corrections

The dataset may be updated or corrected in the following circumstances:

* A corrected annual securities report is filed
* An extraction or classification error is identified
* The normalization rules are revised
* Additional historical data is added
* A numerical value is corrected following comparison with the original disclosure

Material changes will be recorded in the GitHub commit history or release notes.

## 13. Disclaimer

This dataset was independently created from publicly available corporate disclosure documents.

Reasonable efforts have been made to ensure accuracy and completeness. However, no guarantee is made that the dataset is free from errors or omissions.

This dataset should not be used as the sole basis for investment, financial, legal, or other important decisions.

Users should verify important figures against the original disclosures published by each company.


Methodology / データ作成方法
日本語
1. データセットの概要

本データセットは、日本の電力会社が有価証券報告書等で開示している原価・費用明細を、会社間および年度間で比較できるように整理・正規化したものです。

主に、以下のような電気事業に関連する費用項目を収録しています。

燃料費
購入電力料
人件費
修繕費
減価償却費
水利使用料
委託費
賃借料
原子力発電施設解体費
その他の電気事業営業費用の
各費用科目の内訳項目

会社ごとに異なる項目名や表記を可能な範囲で統一し、横断的に分析できる形式にしています。

2. データソース

データは、各社が公開している有価証券報告書の電気事業営業費用明細表です。

原資料は、金融庁のEDINETで公開されている各社の提出書類です。

本データセットは、各電力会社による公式データセットではなく、公開資料をもとに独自に作成したものです。

3. データの抽出方法

数値は、有価証券報告書に含まれる表から抽出しています。

本文内の見出しの階層構造、行名、列名、対象期間、単位、表内の階層関係などを利用して、各数値の意味を判定しています。

数値の抽出および分類には、ルールベースの決定論的な処理を使用しています。生成AIによる数値の推定や補完は行っていません。

4. 対象期間

各年度は、原則として各社の事業年度末を基準としています。

多くの電力会社では、3月31日に終了する年度が対象です。

四半期および中間期の数値は原則として含めず、通期の数値を使用しています。

ただし、会社によって決算期や開示期間が異なる場合があります。年度比較の際には、各レコードの対象期間を確認してください。

5. 連結・個別の取扱い

単体（個別）です。

6. 勘定科目の正規化

原資料では、同じ性質の費用であっても、会社や年度によって異なる名称が使用されています。

例：

燃料費
汽力発電費の燃料費
火力燃料費
原料費
燃料及び購入電力料

横断比較を可能にするため、これらの原文表記を確認したうえで、共通の正規化カテゴリーに分類しています。

正規化カテゴリーの例：

Fuel costs / 燃料費
Purchased power costs / 購入電力料
Personnel expenses / 人件費
Repair and maintenance / 修繕費
Depreciation / 減価償却費
Water usage fees / 水利使用料
Outsourcing expenses / 委託費
Rental expenses / 賃借料
Nuclear-related expenses / 原子力関連費用
Other operating expenses / その他営業費用

正規化後のカテゴリー名は、必ずしも原資料の勘定科目名と完全には一致しません。

原文の項目名を確認できる列がある場合は、正規化カテゴリーと併せて確認してください。

7. 内訳項目の取扱い

本データセットには、勘定科目の合計値だけでなく、その内訳項目が含まれる場合があります。

たとえば「厚生費」の下に、以下のような内訳が開示されることがあります。

・法定厚生費
・一般厚生費

内訳項目は、親となる勘定科目の構成要素です。

したがって、親項目と内訳項目を同時に単純合計すると、同じ費用を二重に計上する可能性があります。

分析目的に応じて、以下のいずれかを選択してください。

勘定科目の合計値のみを使用する
内訳項目のみを使用する
親子関係を確認したうえで集計する

重要な注意

カテゴリー列には、勘定科目の合計値と内訳項目の両方が含まれる場合があります。

データ全体を単純に合計しても、会社全体の原価や営業費用にはなりません。




8. 欠損値とゼロ

空欄は、必ずしもゼロを意味しません。

空欄となる主な理由は以下のとおりです。

当該項目が開示されていない
当該年度に該当する費用が存在しない
他の勘定科目に含まれている
原資料から信頼できる形で特定できなかった
開示区分が変更された
比較可能なデータが存在しない

明示的にゼロと開示されている場合、または原資料からゼロであることが確認できる場合のみ、原則として 0 を入力しています。

空欄をゼロに置き換えて分析すると、費用の過小評価につながる可能性があります。

9. 会社間比較の注意点

各社の発電構成や事業構造は異なります。

たとえば、以下の違いがあります。

水力・火力・原子力・再生可能エネルギーの構成
自社発電と購入電力の割合
送配電事業の分離状況
発電事業会社や燃料調達会社の連結範囲
JERAなど共同出資会社の取扱い
電気事業以外の事業の有無
原子力発電所の廃止措置状況

したがって、金額の単純比較だけでなく、発電量、販売電力量、電源構成などと併せて分析することを推奨します。

10. データ検証

データは、主に以下の方法で検証しています。

原資料に表示された合計値との比較
内訳合計と勘定科目合計の比較
同一会社・同一年度・同一カテゴリーの重複確認
単位および対象期間の確認
隣接年度との連続性確認
原文項目と正規化カテゴリーの対応確認
大幅な増減や外れ値の確認
重要な差異の目視確認

ただし、すべてのレコードについて完全な正確性を保証するものではありません。

11. データの制約

本データセットには、以下の制約があります。

会社ごとに開示形式が異なります。
同じ会社でも年度によって表の構造が変わることがあります。
正規化カテゴリーは分析用に独自に設定したものです。
一部の項目は、複数カテゴリーに分類可能な場合があります。
原資料で内訳の一部しか開示されていない場合があります。
合計値と内訳値は、集計範囲が一致しない場合があります。
セグメント再編や会社分割により、年度間の比較可能性が低下する場合があります。
正規化によって、原文に含まれる細かな会計上の違いが失われる場合があります。

重要な判断を行う際は、必ず原資料を確認してください。

12. 更新と訂正

以下の場合、データを更新または訂正することがあります。

訂正有価証券報告書が提出された場合
分類または抽出上の誤りが見つかった場合
正規化ルールを見直した場合
過年度データを追加した場合
原資料との照合により数値を修正した場合

主な変更は、GitHubのコミット履歴またはリリースノートに記録します。

13. 免責事項

本データセットは、公開された企業開示資料をもとに独自に作成したものです。
正確性および完全性の確保に努めていますが、データに誤りや欠落が含まれないことを保証するものではありません。

本データセットは、投資判断、財務判断、法的判断その他の重要な意思決定の唯一の根拠として使用しないでください。

重要な数値については、各社の原資料と照合してください。

正確性および完全性の確保に努めていますが、データに誤りや欠落が含まれないことを保証するものではありません。

本データセットは、投資判断、財務判断、法的判断その他の重要な意思決定の唯一の根拠として使用しないでください。

重要な数値については、各社の原資料と照合してください。
