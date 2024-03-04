<template>
  <h2>ユーザー登録</h2>

  <Form>
    <label for="nickname">ニックネーム</label>
    <Field type="text" id="nickname" class="input-field" name="nickname" rules="required"/>
    <ErrorMessage name="nickname" class="error-message"/>
    
    <label for="email">メールアドレス</label>
    <Field type="email" id="email" class="input-field" name="email" rules="required|email"/>
    <ErrorMessage name="email" class="error-message"/>

    <label for="password">パスワード</label>
    <Field type="password" id="password" name="password" class="input-field" rules="required|min:6"/>
    <ErrorMessage name="password" class="error-message"/>

    <label for="password-confirmation">確認用パスワード</label>
    <Field type="password" id="password-confirmation" name="password-confirmation" class="input-field" rules="required|confirmed:@password"/>
    <ErrorMessage name="password-confirmation" class="error-message"/>

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
    ErrorMessage
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
  margin-bottom: 8px;
}

#submit-btn {
  width: 160px;
}

.error-message {
  color: red;
}
</style>