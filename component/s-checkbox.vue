<script lang="ts" setup>

import IconCheck from '~/assets/check.svg'

const props = defineProps<{
  modelValue: boolean,
  error: boolean
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void
}>()
</script>

<template>
  <label :class="{error:error}">

    <input
        :checked="modelValue"
        type="checkbox"
        @change="$emit('update:modelValue', $event.target.checked)"
    />
    <icon-check v-show="modelValue"/>

  </label>
  <slot></slot>
</template>

<style lang="scss" scoped>
input[type=checkbox] {
  height: 0;
  width: 0;
  visibility: hidden;
}

label {
  cursor: pointer;
  width: 19px;
  height: 17px;
  background: rgba(122, 151, 255, 0.52);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
  position: relative;
}


label:has(input:checked) {
  background: #3586FF;
}

label.error {
  outline: 1px solid red;
}

::v-deep {
  .nuxt-icon {
    position: absolute;
    z-index: 2;
    width: 9px;
    height: 7px;

    * {
      fill: white;
    }
  }
}
</style>