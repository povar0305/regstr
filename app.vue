<template>
  <div class="wrapper">
    <s-registr v-show="!sendForm" @send="send"/>
    <div v-show="sendForm" class="success">Ваши данные успешно отправлены</div>
  </div>
</template>

<style lang="scss">

body {
  margin: 0;
}
</style>
<style lang="scss" scoped>
.wrapper {
  padding: 1rem;
  background: rgba(73, 39, 39, 0.08);
}
</style>
<script lang="ts" setup>
import SRegistr from "~/component/s-registr.vue";

const sendForm = ref(false)

function send(form) {
  console.log(form)
}
</script>