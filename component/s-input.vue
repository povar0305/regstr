<script lang="ts" setup>
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


const error = ref(false)

function validateInput() {

}
</script>

<template>
  <div class="wrapper">
    <input :class="{error:error}"
           :placeholder="placeholder" :type="password?'password':'text'" :value="props.modelValue"
           @input="$emit('update:modelValue',$event.target.value)">

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

}
</style>