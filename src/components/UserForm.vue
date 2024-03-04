<template>
  <h2>ユーザー登録</h2>
  <form>
    <label for="nickname">ニックネーム</label>
    <input type="text" id="nickname" class="input-field">

    <label for="email">メールアドレス</label>
    <input type="email" id="email" class="input-field">

    <label for="password">パスワード</label>
    <input type="password" id="password" class="input-field">

    <label for="password-confirmation">確認用パスワード</label>
    <input type="password" id="password-confirmation" class="input-field">

    <input type="submit" value="登録" id="submit-btn">
  </form>
</template>

<script>
export default {
  name: 'UserForm',
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