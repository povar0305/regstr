<script lang="ts" setup>

import SInput from "~/component/s-input.vue";

const form = ref({
  name: '',
  email: '',
  password: '',
  password_repeat: '',
  post: '',
  role: null

})
</script>

<template>
  <div class="form">
    <div class="title">
      Регистрация
    </div>
    <div class="inner">
      <div class="text">Заполните Ваши данные</div>
      <div class="inputs">
        <s-input v-model.trim="form.name" placeholder='Имя'/>
        <s-input v-model.trim="form.email" email placeholder='Email'/>
        <s-input v-model.trim="form.password" password placeholder='Пароль'/>
        <s-input v-model.trim="form.password_repeat" password placeholder='Повторите пароль'/>
      </div>
    </div>

    {{ form }}
  </div>

</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.form {
  background: white;
  border-radius: 15px;

  .title {
    font-family: Montserrat;
    font-size: 19px;
    font-weight: 700;
    line-height: 27px;
    letter-spacing: -0.0035em;
    text-align: left;
    padding: 17px 31px;
    border-bottom: 1px solid #D9D9D9;
  }

  .inner {
    display: flex;
    gap: 34px;
    flex-direction: column;
    padding: 17px 31px;

    .text {
      font-family: Montserrat;
      font-size: 16px;
      font-weight: 500;
      line-height: 19px;
      letter-spacing: 0em;
      text-align: left;

    }
  }

  .inputs {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    column-gap: 14px;
    row-gap: 31px;
  }
}


</style>