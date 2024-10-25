# Vue.js メールフォームコンポーネント

このコンポーネントは、Vue.jsを使用して作成されたメールフォームです。ユーザーが報告者、入出タイプ、およびアポイント情報を入力でき、送信時にEmailJSを通じてメールを送信します。

## 機能

- 報告者の選択（ドロップダウン）
- 入出タイプの選択（ドロップダウン）
- アポイント情報の入力（テキスト入力）
- フォーム送信時にEmailJSを通じてメール送信

## セットアップ

このコンポーネントを使用するには、以下の設定が必要です：

1. EmailJSアカウントの作成とサービスの設定
2. `@/config/AppSettings.js` ファイルにEmailJS関連の設定を追加：
   - `emailjsServiceId`
   - `emailjsTemplateId`
   - `emailjsUserId`

## 使用方法

1. コンポーネントをVue.jsプロジェクトにインポートします。
2. 必要な場所にコンポーネントを配置します。

```vue
<template>
  <MailSlot />
</template>

<script>
import MailSlot from '.@/MailSlot.vue'

export default {
  components: {
    MailSlot
  }
}
</script>
