<script lang="ts" setup>
const selected = ref('A')

const options = ref([
  {text: 'One', value: 'A'},
  {text: 'Two', value: 'B'},
  {text: 'Three', value: 'C'}
])

</script>

<template>

  <select v-model="selected">
    <option v-for="option in options" :value="option.value">
      {{ option.text }}
    </option>
  </select>
</template>

<style lang="scss" scoped>

</style>