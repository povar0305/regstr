<script lang="ts" setup>

import IconShowed from '~/assets/showed.svg'
import IconHided from '~/assets/hided.svg'

const props = withDefaults(defineProps<{
  modelValue: string
  password?: boolean
  placeholder?: string
  email?: boolean
}>(), {
  password: false,
  email: false
})
const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void
}>()


const showPassword = ref(true)
const error = ref({status: false, text: ''})
const regex = new RegExp('[a-z0-9]+@[a-z]+\.[a-z]{2,3}');

function validateInput(event) {
  console.log(event)
  if (event.target.value == '') {
    error.value.status = true
    error.value.text = 'Заполните поле'
  }

  if (props.email && !regex.test(event.target.value)) {
    error.value.status = true
    error.value.text = 'Введите корректный email'
  }
  emit('update:modelValue', event.target.value)
}


</script>

<template>
  <div class="wrapper">
    <input :class="{error:error.status}"
           :placeholder="placeholder" :type="password&&showPassword?'password':'text'" :value="modelValue"
           @blur="validateInput" @focus="error.status=false" @input="$emit('update:modelValue', $event.target.value)">

    <icon-showed v-show="password&&!showPassword" class="icon" @click="showPassword=!showPassword"/>
    <icon-hided v-show="password&&showPassword" class="icon" @click="showPassword=!showPassword"/>
    <span v-show="error.status" class="error-text">
    {{ error.text }}
    </span>
  </div>

</template>

<style lang="scss" scoped>
.error {
  border-color: red;
}

input {
  font-family: Montserrat;
  font-size: 14px;
  font-weight: 400;
  line-height: 19px;
  letter-spacing: -0.0015em;
  text-align: left;
  color: #9292A0;
  padding: 10px;
  outline: none;
  border-radius: 11px;
  border: 1px solid #E6E6EB;
  width: 100%;
}

.wrapper {
  position: relative;
  display: flex;
}

::v-deep {
  .nuxt-icon--fill {
    position: absolute;
    right: 13.22px;
    width: 21px;
    top: 14px;
    cursor: pointer;

    * {
      fill: #A4A4A6;
    }
  }
}

.error-text {
  color: red;
  bottom: -17px;
  font-family: Montserrat;
  font-size: 14px;
  position: absolute;
}
</style>