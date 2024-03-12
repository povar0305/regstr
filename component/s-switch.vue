<template>
  <label>
    <input
        :checked="modelValue"
        type="checkbox"
        @change="$emit('update:modelValue', $event.target.checked)"
    />
  </label>
  <slot></slot>
</template>
<script lang="ts" setup>
const props = defineProps<{
  modelValue: boolean
}>()


const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void
}>()
</script>

<style lang="scss" scoped>


input[type=checkbox] {
  height: 0;
  width: 0;
  visibility: hidden;
}

label {
  cursor: pointer;
  text-indent: -9999px;
  width: 39px;
  height: 19px;
  background: rgba(122, 151, 255, 0.52);
  display: block;
  border-radius: 100px;
  position: relative;
}

label:after {
  content: '';
  position: absolute;
  top: -0.5px;
  left: 0px;
  width: 17px;
  height: 17px;
  background: #fff;
  border-radius: 90px;
  transition: 0.2s;
  border: 0.5px solid #CDCED8;
}

label:has(input:checked) {
  background: #3586FF;

  &:after {
    left: calc(100%);
    transform: translateX(-100%);
  }
}

label:active:after {
  width: 39px;
}
</style>