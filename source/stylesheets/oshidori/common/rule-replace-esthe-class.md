/*
---
name: Estheのclass名しか付与されていない箇所のOshidori置換ルール
tag:
  - rule
  - temporary-rule-when-replace-esthe-to-oshidori
category:
  - 0_rule
  - 0_rule/temporary-rule
  - 0_rule/temporary-rule/rule-replace-esthe-class
---

EstheのクラスをOshidoriのmixinに置換する時、一意のクラス名が付与されていない場合は、暫定処置として `.unnamed-block-` `.unnamed-element-` を付与する。

- 一時的な命名のため、適切な名前を付与する必要がある。
- その旨をTODOコメントとして追記する。

## 一意のクラス名がついている親要素の子孫としてEstheクラスがある場合

- 親block の `unnamed-element` としてクラスを作成する。
- 親要素のSCSSファイルに追加する。

### 命名ルール

`.(一意のクラス名)__unnamed-element-(ナンバリング)`

### 置換前

```
%ul.esthe-example-list
  %li.column-align-center
    %span.layout-base.column-high-priority
  %li.column-align-center.mg5b
    %span.layout-base.column-high-priority
```

```scss
.esthe-example-list {
  margin: 0;
}
```

### 置換後


```
-# TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
%ul.esthe-example-list
  %li.esthe-example-list__unnamed-element1
    %span.esthe-example-list__unnamed-element2
  %li.esthe-example-list__unnamed-element3
    %span.esthe-example-list__unnamed-element2
```

```scss
.esthe-example-list {
  margin: 0;

  // TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
  .esthe-example-list__unnamed-element1 {
    align-items: center;
  }

  // TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
  .esthe-example-list__unnamed-element2 {
    @include layout-flexbox;
    flex: 1;
  }

  // TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
  .esthe-example-list__unnamed-element3 {
    @include os1-set-margin($margin-side: bottom, $margin-size: XS);
    align-items: center;
  }
}
```


## 親要素がなくEstheクラスがある場合

- 仮block `unnamed-block` の `unnamed-element` としてクラスを作成する。
- 置換したSCSSファイルは `stylesheets/[ pc | smartphone ]/[ 置換元のSCSSディレクトリ ]/_unnamed-blocks.scss` に置く。
- ファイルは移植元のSCSSファイルがある親ディレクトリの直下に置く。

### 命名ルール

block: `.unnamed-block-(置換するhamlディレクトリ名)-(置換するhamlファイル名)` 

element: `.unnamed-block-(置換するhamlディレクトリ名)-(置換するhamlファイル名)__unnamed-element-(ナンバリング)`

### 置換前

`app/views/sample_directory/sample_file.html.haml`

```
%ul.column-align-center
  %li.column-align-center
    %span.layout-base.column-high-priority
```

### 置換後

`app/views/sample_directory/sample_file.html.haml`

```
-# TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
%ul.unnamed-block-sample_directory-sample_file
  %li.unnamed-block-sample_directory-sample_file__unnamed-element1
    %span.unnamed-block-sample_directory-sample_file__unnamed-element2
```

`app/assets/stylesheets/pc/sample_directory/_unnamed-blocks.scss`

```scss
// TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
.unnamed-block-sample_directory-sample_file {
  align-items: center;

  .unnamed-block-sample_directory-sample_file__unnamed-element1 {
    align-items: center;
  }

  .unnamed-block-sample_directory-sample_file__unnamed-element2 {
    @include layout-flexbox;
    flex: 1;
  }
}
```

### 置換前

`app/views/sample_directory/sample_child_directory/sample_file.html+smartphone.haml`

```
%ul
  %li.column-align-center
    %span.layout-base.column-high-priority
```

### 置換後

`app/views/sample_directory/sample_child_directory/sample_file.html+smartphone.haml`

```
-# TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
%ul.unnamed-block-sample_directory-sample_child_directory-sample_file
  %li.unnamed-block-sample_directory-sample_child_directory-sample_file__unnamed-element1
    %span.unnamed-block-sample_directory-sample_child_directory-sample_file__unnamed-element2
```

`app/assets/stylesheets/smartphone/sample_directory/_unnamed-blocks.scss`

```scss
// TODO: unnamed-はOshidoriスタイル置換時の一時的な命名です。適切な名前を付与してください。
.unnamed-block-sample_directory-sample_child_directory-sample_file {

  .unnamed-block-sample_directory-sample_child_directory-sample_file__unnamed-element1 {
    align-items: center;
  }

  .unnamed-block-sample_directory-sample_child_directory-sample_file__unnamed-element2 {
    @include layout-flexbox;
    flex: 1;
  }
}
```
*/
