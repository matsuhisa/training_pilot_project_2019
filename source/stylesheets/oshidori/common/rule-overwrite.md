/*
---
name: Oshidoriスタイルの追記・上書きルール
tag:
  - rule
category:
  - 0_rule
  - 0_rule/rule-overwrite
---

## Oshidoriスタイルの追記・上書きルール

Oshidoriのスタイルをディレクトリ別で独自に追記・上書きしたい時は以下のルールに従う。

- 追記・上書きするための scss ファイルは `stylesheets/[pcもしくはsmartphone]/[上書きしたいコンポーネントのあるディレクトリ名]/_p-[ディレクトリ名]-[上書きしたいコンポーネント名]-[ナンバリング].scss` に置く
  - 例）review-ranking内のあるページで alert-label のスタイルを追記・上書きしたい場合、 `stylesheets/pc/review-ranking/_p-review-ranking-alert-label-1.scss` に置く
  - 追記・上書き用のファイルが一つしかない場合でも、ファイル名にナンバリングを必ず付与する
  - 同ディレクトリ内で既に上書きされているコンポーネントを別のスタイルで上書きする必要が出てきた場合、ナンバリングを上げてファイルを作成する (`stylesheets/pc/review-ranking/_p-review-ranking-alert-label-2.scss`)
- 追記・上書きしたいコンポーネント毎にファイルを作る
  - 例）PC版スタイルの alert-label と any-label のスタイルを上書きしたい時は `stylesheets/pc/review-ranking/_p-review-ranking-alert-label-1.scss` と `stylesheets/pc/review-ranking/_p-review-ranking-any-label-1.scss` というふうに別々にファイルを作成する
- p-[ディレクトリ名]-[コンポーネント名]というクラス名で追記・上書きする

例）
```scss
//stylesheets/pc/review-ranking/_p-review-ranking-alert-label-1.scss

.p-review-ranking-alert-label-1 {
  //追記・上書きするスタイル
}
```
- 同じディレクトリ内に複数ある同じコンポーネントに別々にスタイルを追記・上書きしたい場合、別々にファイルとクラスを作成してナンバリングする

例）
```html 
<div class="dummy-box">
  <span class="os1-alert-label p-review-ranking-alert-label-1">受付終了</span>
</div>
…
<p>
  <span class="os1-alert-label p-review-ranking-alert-label-2">終了</span>
  texttext
</p>
```
```scss
// stylesheets/pc/review-ranking/_p-review-ranking-alert-label-1.scss に以下を書く
span.p-review-ranking-alert-label-1 {
  margin-right: 23px;

  .p-review-ranking-alert-label-1__element {
    display: block;
  }
}
```
```scss
// stylesheets/pc/review-ranking/_p-review-ranking-alert-label-2.scss に以下を書く
span.p-review-ranking-alert-label-2 {
      display: block;
}
```
*/
