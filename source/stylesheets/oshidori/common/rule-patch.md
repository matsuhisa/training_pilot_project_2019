/*
---
name: Estheスタイルの上書き 移植ルール
tag:
  - rule
  - temporary-rule-when-replace-esthe-to-oshidori
category:
  - 0_rule
  - 0_rule/temporary-rule
  - 0_rule/temporary-rule/rule-patch
---

Estheのクラスを上書きしている場合は、暫定処置として `.patch-`を付与し `_patch.scss` に移植する。

- 移植先のファイルには移植元のファイル名をNOTEコメントとして追記する。
- 移植元のファイルには移植先のファイル名と使用箇所を確認したのち削除できる旨をNOTEコメントとして追記する。

### 移植先のSCSSファイルのディレクトリ配置

- 移植先のSCSSファイルは `stylesheets/[ pc | smartphone ]/[ 移植元のSCSSディレクトリ ]/_patch.scss` に置く。
- ファイルは移植元のSCSSファイルがある親ディレクトリの直下に置く。
- 例1）`stylesheets/pc/places/_sample.scss` に書かれたクラス移植は `stylesheets/pc/places/_patch.scss` に追加する
- 例2）`stylesheets/smartphone/places/cost/_sample.scss` に書かれたクラス移植は `stylesheets/smartphone/places/_patch.scss` に追加する

### 命名ルール

`.patch-(移植元のSCSSディレクトリ名)-(移植元のSCSSファイル名)-(上書きしていたEstheクラス名)-(ナンバリング)`

### 置換前

`app/views/sample_directory/sample_file.html.haml`

```
.sample-block
  %span.sample-block__sample-element
    %span.symbol-crown
```

`app/assets/stylesheets/pc/sample_directory/sample_child_directory/sample_file.scss`

```scss
.sample-block {
  &__sample-element {
    margin: 0;
    .symbol-crown {
      margin-top: -4px;
    }
  }
}
```

### 置換後

`app/views/sample_directory/sample_file.html.haml`

```
.sample-block
  %span.sample-block__sample-element
    %span.os1-symbol-crown.patch-sample_directory-sample_child_directory-sample_file-symbol-crown-1
```

`app/assets/stylesheets/pc/sample_directory/sample_child_directory/sample_file.scss`

```scss
.sample-block {
  &__sample-element {
    margin: 0;
    // NOTE: app/assets/stylesheets/pc/sample_directory/_patch.scss に移植済み。
    // Oshidori移行後、使用箇所をすべて確認し問題なければ削除できます。
    .symbol-crown {
      margin-top: -4px;
    }
  }
}
```

`app/assets/stylesheets/pc/sample_directory/_patch.scss`

```scss
// NOTE: app/assets/stylesheets/pc/sample_directory/sample_child_directory/sample_file.scss より切り出し
.patch-sample_directory-sample_child_directory-sample_file-symbol-crown-1 {
  margin-top: -4px;
}
```
*/
