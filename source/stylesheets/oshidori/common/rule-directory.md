/*
---
name: Oshidori ディレクトリ構成
tag:
  - rule
category:
  - 0_rule
  - 0_rule/directory
---

## Oshidori 内ディレクトリ構成

```
- 📁oshidori root
  - 📁common
    - 📁components # 汎用コンポーネント系class
      - 📁buttons
      - 📁forms
      - 📁...
    - 📁layouts # 汎用レイアウト系class
    - 📁variables # 変数・mixin
```

## Oshidoriスタイルの拡張 scss の格納場所
([Oshidoriスタイルの追記・上書きルール](/styleguide/category/0_rule/rule-overwrite/index.html)を参照)

```
- 📁stylesheets
  - 📁pc
    - 📁review_ranking
      - 🗒_p-review-ranking-[コンポーネント名]-[ナンバリング].scss
      - 🗒_p-review-ranking-alert-label-1.scss
      - 🗒_p-review-ranking-alert-label-2.scss
      - 🗒_p-review-ranking-any-label-1.scss
      - 🗒...
    - 📁feature
      - 🗒_p-feature-[コンポーネント名]-[ナンバリング].scss
      - 🗒...
    - 📁...
  - 📁smartphone
    - 📁review_ranking
      - 🗒_p-review-ranking-[コンポーネント名]-[ナンバリング].scss
      - 🗒...
    - 📁feature
    - 📁...
```
*/
