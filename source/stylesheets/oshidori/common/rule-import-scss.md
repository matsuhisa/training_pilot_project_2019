/*
---
name: Oshidori外のSCSSファイルの読み込みについて
tag:
  - rule
category:
  - 0_rule
  - 0_rule/rule-import-scss
---

## Oshidori外のSCSSファイルの読み込みについて

Oshidori外のディレクトリ固有のSCSSファイルについては以下のルールに従って作成する。

- 適用するページのディレクトリ内 (例:`app/assets/stylesheets/pc/review_ranking`) に、 1 Block 1 ファイル としてSCSSファイルを作成する
- ファイル名は Block 名と同じにする
- ディレクトリ内のSCSSファイルを一括で読み込みたい場合は、 `@import 'pc/review_ranking/*'` という風に一括指定して読み込む

例）
```scss
//stylesheets/pc/review-ranking/_review-ranking-condition.scss
.review-ranking-condition {
  position: relative;
  margin: 10px 0 20px;
  ...
}
```

```scss
//stylesheets/pc/review-ranking/_review-ranking-food-list.scss
.review-ranking-food-list {
  li {
    float: left;
    width: 33.3%;
    box-sizing: border-box;
    text-align: center;
    a {
      display: block;
      @include set_anchor($navy);
    }
    ...
  }
  &.m--top-5 {
    ...
  }
}
```
*/
