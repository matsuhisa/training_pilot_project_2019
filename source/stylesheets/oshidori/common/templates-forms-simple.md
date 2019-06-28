/*
---
name: Oshidori フォーム シンプルなフォームのテンプレート
tag:
  - templates
category:
  - 4_templates
  - 4_templates/forms
  - 4_templates/forms/simple
---

## シンプルなフォームのテンプレート例

- ブライダルフェア予約フォームや、サービスへのお問い合わせなどのフォームでの利用を想定しています
- テキスト、表示要素はダミーです。表示順や表示要素を確認してください
  - Rails の helper による生成になるので使用している class に着目してください
- レスポンシブでの利用を想定しています。動作確認の時は、スマートフォン、PCどちらとも確認をお願いします

### NOTE

- Rails の layouts/formが使われる想定です。ヘッダーやフッターがフォーム以外のページへ遷移しないようなデザインになっているからです
- ❗ 口コミ投稿フォームのような複雑な入力内容や、写真だけを投稿するような特別な用途での利用は想定していません
  - シンプルなフォームのテンプレートに部分的な追加をして利用するのは問題ありません

### 入力画面

```html
<div class="os1-content">

  <div class="os1-form-title">
    <h1 class="os1-title -h1">お問い合わせフォーム</h1>
  </div>

  <ol class="os1-status-bar">
    <li class="os1-status-bar__item-wrapper" aria-current="step">
      <div class="os1-status-bar__item">
        <span class="os1-status-bar__step-number">1</span>
        <span class="os1-status-bar__step-text">入力</span>
      </div>
    </li>
    <li class="os1-status-bar__item-wrapper">
      <div class="os1-status-bar__item">
        <span class="os1-status-bar__step-number">2</span>
        <span class="os1-status-bar__step-text">確認</span>
      </div>
    </li>
    <li class="os1-status-bar__item-wrapper">
      <div class="os1-status-bar__item">
        <span class="os1-status-bar__step-number">3</span>
        <span class="os1-status-bar__step-text">完了</span>
      </div>
    </li>
  </ol>

  <form>

    <div class="os1-form-body">
      <p>
      「みんなのウェディング」をご利用いただいている上で、分からないことや困ったことがあった場合は、まず、「よくある質問＆回答（FAQ）」をお読みください。 <br>
      それでも問題が解決しない場合は、こちらのフォームからお問い合わせください。
      </p>

      <div class="os1-alert-text -error -margin-top-M">
        メールアドレスまたはパスワードが正しくありません
      </div>

      <div class="os1-form-group">
        <h3 class="os1-form-group__title -margin-top-M">
          <label>お問い合わせ内容</label>
        </h3>
        <h4 class="os1-form-group__sub-title">
          <span class="os1-must-label">必須</span>
          <label>メールアドレス</label>
        </h4>
        <div class="os1-form-group__caption">
          ドメイン指定受信を設定されている方は[mwed.jp]と[edmont.co.jp]のドメインからのメールを受信できるよう設定してください。
        </div>
        <div class="os1-form-group__input">
          <div class="os1-default-mail-field -size-L-pc-only">
            <input class="os1-default-mail-field__input" placeholder="minnano.shiho@mwed.co.jp" type="email" name="foo" id="os1-foo-1">
          </div>
        </div>
        <h4 class="os1-form-group__sub-title">
          <span class="os1-must-label">必須</span>
          <label>名前</label>
        </h4>
        <div class="os1-form-group__input">
          <label class="os1-default-text-field">
            <span class="os1-default-text-field__text -margin-right-S">姓</span>
            <input class="os1-default-text-field__input" placeholder="皆野" type="text" name="foo">
          </label>
          <label class="os1-default-text-field">
            <span class="os1-default-text-field__text -margin-right-S">名</span>
            <input class="os1-default-text-field__input" placeholder="志穂" type="text" name="foo">
          </label>
        </div>
        <h4 class="os1-form-group__sub-title">
          <span class="os1-any-label">任意</span>
          <label>問い合わせ内容</label>
        </h4>
        <div class="os1-form-group__input">
          <div class="os1-default-checkbox">
            <label>
              <input class="os1-default-checkbox__input" type="checkbox" name="foo" value="foo1">
              <span class="os1-default-checkbox__text">式場探し</span>
            </label>
          </div>
          <div class="os1-default-checkbox">
            <label>
              <input class="os1-default-checkbox__input" type="checkbox" name="foo" value="foo1">
              <span class="os1-default-checkbox__text">結婚式レポ</span>
            </label>
          </div>
          <div class="os1-default-checkbox">
            <label>
              <input class="os1-default-checkbox__input" type="checkbox" name="foo" value="foo1">
              <span class="os1-default-checkbox__text">花嫁Q&A</span>
            </label>
          </div>
        </div>
      </div>

      <div class="os1-form-group">
        <h3 class="os1-form-group__title">
          <label>アンケート</label>
        </h3>
        <h4 class="os1-form-group__sub-title">
          <span class="os1-any-label">任意</span>
          <label>年齢</label>
        </h4>
        <div class="os1-form-group__input">
          <div class="os1-default-radio">
            <label>
              <input class="os1-default-radio__input" type="radio" name="foo" value="foo1">
              <span class="os1-default-radio__text">20〜30代</span>
            </label>
          </div>
          <div class="os1-default-radio">
            <label>
              <input class="os1-default-radio__input" type="radio" name="foo" value="foo1">
              <span class="os1-default-radio__text">30〜40代</span>
            </label>
          </div>
          <div class="os1-default-radio">
            <label>
              <input class="os1-default-radio__input" type="radio" name="foo" value="foo1">
              <span class="os1-default-radio__text">40代〜50代</span>
            </label>
          </div>
        </div>
      </div>

      <div class="os1-horizontal-button-group">
        <div class="os1-primary-button -size-L">
          <button type="button" class="os1-primary-button__item">
            <span class="os1-primary-button__text">確認する</span>
          </button>
        </div>
      </div>

    </div>

  </form>

</div>
```

*/
