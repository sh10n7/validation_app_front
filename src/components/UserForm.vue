<template>
  <h2>ユーザー登録</h2>
  <!-- <Form>コンポーネントを使用して、Fieldコンポーネントを囲む -->
  <Form>
    <label for="nickname">ニックネーム</label>
    <!-- Fieldコンポーネントを使用して、入力フォームを作成する -->
    <Field type="text" id="nickname" class="input-field" />

    <label for="email">メールアドレス</label>
    <Field type="email" id="email" class="input-field" />

    <label for="password">パスワード</label>
    <Field type="password" id="password" class="input-field" />

    <label for="password-confirmation">確認用パスワード</label>
    <Field type="password" id="password-confirmation" class="input-field" />

    <input type="submit" value="登録" id="submit-btn">
  </Form>
</template>

<script>
import { Form, Field } from 'vee-validate';

export default {
  name: 'UserForm',
  components: {
    Form,
    Field,
  }
}

</script>

<style>
form {
  display: flex;
  flex-direction: column;
  width: 320px;
}

.input-field {
  padding: 8px;
  margin-bottom: 16px;
}

#submit-btn {
  width: 160px;
}
</style>