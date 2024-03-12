<script lang="ts" setup>

import SInput from "~/component/s-input.vue";
import SSelect from "~/component/s-select.vue";
import SSwitch from "~/component/s-switch.vue";
import SButton from "~/component/s-button.vue";
import SCheckbox from "~/component/s-checkbox.vue";

const form = ref({
  username: '',
  email: '',
  password: '',
  password_repeat: '',
  post: '',
  role: null,
  public: false

})

const roles = [
  {value: 0, name: 'Должность 1'},
  {value: 3, name: 'Должность 3'},
  {value: 5, name: 'Должность 6'},
  {value: 10, name: 'Должность 8'}
]

const checkRole = ref(false);
const policy = ref(true)

const validePolice = ref(true)

function registr() {
  validePolice.value = policy.value
  console.log('registr')

}
</script>

<template>
  <div class="form">
    <div class="title">
      Регистрация
    </div>
    <div class="inner">
      <div class="text">Заполните Ваши данные</div>
      <div class="inputs">
        <s-input v-model.trim="form.username" placeholder='Имя'/>
        <s-input v-model.trim="form.email" email placeholder='Email'/>
        <s-select v-model="form.role" :data="roles" :error="checkRole" placeholder="Должность"/>
        <s-input v-model.trim="form.password" password placeholder='Пароль'/>
        <s-input v-model.trim="form.password_repeat" password placeholder='Повторите пароль'/>
      </div>
    </div>
    <div class="footer">
      <div class="item">
        <div class="row">
          <s-switch v-model="form.public"/>
          <div class="texts">
            <p class="switch-title">Хотите чтобы Ваш профиль видели другие участники платформы? </p>
            <p class="switch-text">Включает профиль для просмотра другими пользователями по ссылке</p>
          </div>
        </div>
      </div>
      <div class="item">
        <div class="col">
          <s-checkbox v-model="policy" :error="!validePolice" @update:modelValue="validePolice=true"/>
          <p class="policy-text">Регистрируясь, Вы соглашаетесь с политикой конфиденциальности и обработкой персональных
            данных</p>
        </div>
        <div class="col">
          <s-button @click="registr">
            Зарегистрироваться
          </s-button>
        </div>
      </div>
    </div>
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

.footer {
  padding: 23px 31px;
  border-top: 1px solid #D9D9D9;

  .item {
    display: flex;
    justify-content: space-between;

    .row {
      display: flex;
      gap: 5px;

      .texts {
        display: flex;
        flex-direction: column;
        gap: 10px;

        p {
          margin: 0;
          font-family: Montserrat;
          font-size: 14px;
          font-weight: 400;
          line-height: 19px;
          letter-spacing: -0.0015em;
          text-align: left;
        }

        .switch-title {
          font-size: 16px;
          font-weight: 500;
          letter-spacing: 0em;
        }
      }
    }


  }
}

::v-deep {
  .s-button {
    font-family: Montserrat;
    font-size: 12px;
    font-weight: 400;
    line-height: 19px;
    letter-spacing: -0.0015em;
    text-align: left;
    color: #497ADA
  }
}
</style>