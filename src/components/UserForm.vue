<template>
  <h2>ユーザー登録</h2>

  <Form>
    <label for="nickname">ニックネーム</label>
    <!-- 必須(required)のバリデーション追加 -->
    <Field type="text" id="nickname" class="input-field" name="nickname" rules="required"/>
    

    <label for="email">メールアドレス</label>
    <!-- 必須(required)、emailに関するバリデーション追加 -->
    <Field type="email" id="email" class="input-field" name="email" rules="required|email"/>

    <label for="password">パスワード</label>
    <!-- 必須(required)、最小文字数に関するバリデーション追加 -->
    <Field type="password" id="password" name="password" class="input-field" rules="required|min:6"/>

    <label for="password-confirmation">確認用パスワード</label>
    <!-- 必須(required)、confirmed(確認用フィールドの検証)に関するバリデーション追加 -->
    <Field type="password" id="password-confirmation" name="password-confirmation" class="input-field" rules="required|confirmed:@password"/>

    <input type="submit" value="登録" id="submit-btn">
  </Form>
</template>

<script>
import { Form, Field, defineRule, ErrorMessage  } from 'vee-validate';
import { required, email, min, confirmed } from '@vee-validate/rules';

defineRule('required', required);
defineRule('email', email);
defineRule('min', min);
defineRule('confirmed', confirmed);

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