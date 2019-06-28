/*
---
name: Oshidori コーディングルール
tag:
  - rule
category:
  - 0_rule
  - 0_rule/rule-coding
---

## ベースのスタイル

Oshidoriは以下をベースとして作成されている。

- Oshidori全体: `app/assets/stylesheets/_reset.scss`
- OshidoriPC版: `app/assets/stylesheets/pc/_common_base.scss`
- OshidoriSP版: `app/assets/stylesheets/smartphone/_common_base.scss`
- これらのscssを読み込んでいないページでOshidoriは使用できない。

## HTML Class 命名指針

- [MindBEMding](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)をベースとする。
- ただし、Modifier は使用せず[ECSS](http://ecss.io/)の名前空間の概念と[RSCSS](http://rscss.io/variants.html)のVariantsを採用する。

### BEM（MindBEMding）+ RSCSS

本来 BEM では `.block__element--modifier` となるが

- class 名が長くなりがち。
- element をまたいで共通の modifier が必要なときに class 名が組み合わせ爆発することがある。

これらを解消するために modifier の命名だけ rscss.io の Variants のルールを利用することとする。
http://rscss.io/variants.html

```css
.[project-namespace]-[block-name]__[element-name].-[modifier]
```

e.g.

```css
.os1-useful-list {...}
.os1-useful-list__item {...}
.os1-useful-list__item.-selected {...}
```

レイアウトやページなどコンポーネントではないクラスは接頭辞を付ける。

```css
//ページ単位で使うものは 接頭辞 `p-`
.p-course-content {...}
.p-search-calender {...}
```

### ❌Bad例
- Oshidoriで利用されているclass名を(Oshidori未使用のページでも)目的以外で利用しない

```css
.another-place-block {
  // NG!
  .os1-default-button {...}

  // OK!
  .another-place-block__another-button {...}
}
```

- Oshidoriで利用されているclass名を上書きしない
  - 上書きしたい時は別のclass名を指定して上書きする（[Oshidori ディレクトリ独自のスタイル追記・上書きルール](/styleguide/category/0_rule/rule-overwrite/index.html)参照）

```css
// NG!
.os1-default-button {
  background-color: black
}

// OK!
.p-review-ranking-default-button-1 {
  background-color: black
}
```

## 変数

`基準値`を変数化する。

- 色
  - Oshidori CSSで使用できるもの
  - 使用用途が限られているもの
  - リンク色と下線
- フォントサイズ
- 余白（margin / padding)
- border / radius
- コンテンツ幅

## WAI-ARIA

- 状態など相応しいWAI-ARIA がある場合はModifierよりもWAI-ARIAを優先して使う。
- https://momdo.github.io/wai-aria-1.1/
- ただし、 js での state 管理上 WAI-ARIA での管理が不適切な場合は厳密に採用しなくてもよい。

(e.g)
- 現在地には`aria-current`
- 選択時には`aria-selected`
- 開閉パネルには`aria-expanded`や`aria-hidden`


## CSS Selectorの書き方
### 基本ルール
``` css
.block {}
.block .block__element {}
.block .block__element:hover,
.block .block__element:active,
.block .block__element:focus,
.block .block__element.-selected {...}
```

### 変則ルール
``` css
.list > li {} # コンポーネント内で完結しかつセマンティックなセレクタのみ、子セレクタのみタイプセレクタを認める
.link > a {} # 同上
```

### ❌Bad例
``` css
.block .block__element__element {...} ## Block__element__elementの禁止
.block li {...} # 子孫セレクタでタイプセレクタを使わない
.block .another-block__element {...} # 違う block の element をネストしない
.block .another-block {...} # block の中に block をネストしない（HTML構造にCSSのネストを合わせる必要はない）
.block__element {...} # block で包含しないセレクタは使わない
li {} # タイプセレクタを単体で使わない（ブラウザ間の差異を吸収する場合に限って可/base.cssに記述すること）
.-selected {...} # modifier を単体で使わない
[aria-hidden] {...} # 属性セレクタを単体で使わない
.block > section,
.block > div,
.block > span {...} # 子セレクタであっても section, div, span 要素を単体で含むセレクタは使用しない
```

## コンポーネントのネスト

- コンポーネント間のネストを可とする。
- ただし、スタイルの指定は「blockに対して」行うものとする。
- 子コンポーネント（element）の修正を行う必要がある場合、別コンポーネントを作成する。

## コンポーネント間の余白

- コンポーネントに余白のmodifierが用意されているものはmodifierを使用する。
- modifierが用意されていない・個別で余白の値を指定したいときは[Oshidori ディレクトリ独自のスタイル追記・上書きルール](/styleguide/category/0_rule/rule-overwrite/index.html)を参照。

## レスポンシブ

Oshidori ではPC・SPのスタイルが同じSCSSファイルに書かれており、表示サイズ768pxを基点に切り替わる。

  - 767px以下 : SP向けスタイル
  - 768px以上 : PC向けスタイル

実際にスタイルガイド上で幅を調整して確認できる。

- SP向けスタイルを基本として書き、レスポンシブ対応用のmixin `@include os1-screen(pc) {}` でPC向けスタイルを上書きする。
- SP向けスタイルとPC向けスタイルが大きく違う場合に限り、`@include os1-screen(pc) {}` と `@include os1-screen(sp) {}`を個別に使用してスタイルを記述する。

## SCSS コーディングルール

- コンポーネント単位でパーシャルを分ける（1ファイル1コンポーネント）。
  - コンポーネント間で依存はしない。
- 煩雑化を防ぐため、**@extendの使用を禁止**する。基本Mixinを使用。
- コンポーネント独自の Mixin はコンポーネントディレクトリにパーシャルで配置する。
- element の指定時に **block名を `&` と省略しない**。
- @include は通常のプロパティより先に記述する。ただし`@include os1-screen` を除く。
- レスポンシブ対応用のmixin `@include os1-screen` は、そのセレクタをオーバーライドしていることが一目で理解出来るように、必ずオーバーライドするセレクタの最後に記述する。

## HTML マークアップルール

- セマンティックとセクショニングを意識しつつ迷ったら`div`。
- 今後、SEO改修なども考えれるので要素が変わってもデザインが崩れないようにする。

## ディレクトリ独自のスタイル上書き・追記について

- [Oshidori ディレクトリ独自のスタイル追記・上書きルール](/styleguide/category/0_rule/rule-overwrite/index.html)を参照。

## Oshidori外のSCSSファイルの読み込みについて

- [Oshidori外のSCSSファイルの読み込みについて](/styleguide/category/0_rule/rule-import-scss/index.html)を参照。

*/
