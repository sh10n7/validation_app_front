<template>
  <h2>ユーザー登録</h2>

  <Form>
    <label for="nickname">ニックネーム</label>
    <Field type="text" id="nickname" class="input-field" name="nickname" v-model="user.nickname" rules="required|japaneseText"/>
    <ErrorMessage name="nickname" class="error-message"/>
    
    <label for="email">メールアドレス</label>
    <Field type="email" id="email" class="input-field" name="email" v-model="user.email" rules="required|email"/>
    <ErrorMessage name="email" class="error-message"/>

    <label for="password">パスワード</label>
    <Field type="password" id="password" name="password" v-model="user.password" class="input-field" rules="required|min:6"/>
    <ErrorMessage name="password" class="error-message"/>

    <label for="password-confirmation">確認用パスワード</label>
    <Field type="password" id="password-confirmation" name="password-confirmation"  v-model="user.password_confirmation" class="input-field" rules="required|confirmed:@password"/>
    <ErrorMessage name="password-confirmation" class="error-message"/>

    <input type="submit" value="登録" id="submit-btn" @click="registerBtn">
  </Form>
</template>

<script>
import { Form, Field, defineRule, ErrorMessage  } from 'vee-validate';
import { required, email, min, confirmed } from '@vee-validate/rules';
import axios from 'axios';
import { ref } from 'vue';

defineRule('required', required);
defineRule('email', email);
defineRule('min', min);
defineRule('confirmed', confirmed);

// 全角ひらがな、カタカナ、漢字のみ許容する独自ルールを追加。valueに入力された値が入る。
defineRule('japaneseText', (value) => {
  // 全角ひらがな、カタカナ、漢字が入力された場合はtrueを返し、含まれない場合はエラーメッセージを表示。
  if (/^[ぁ-んァ-ン一-龥]+$/.test(value)) {
    return true;
  }
  return 'Nickname should be in full-width Hiragana, Katakana, or Kanji characters.'
})

export default {
  name: 'UserForm',
  components: {
    Form,
    Field,
    ErrorMessage
  },
  setup(){
    const user = ref({
      nickname: '',
      email: '',
      password: '',
      password_confirmation: ''
    })

    const registerBtn = async() => {
      try {
        await axios.post('http://localhost:3000/register', user.value);
      }catch(error) {
        console.log('データの保存ができませんでした', error);
      }
    }
    return { user, registerBtn }
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