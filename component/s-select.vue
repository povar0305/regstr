<script lang="ts" setup>

const props = defineProps<{
  modelValue: number
  data: [{ value: number, name: string }]
  placeholder: string
  error: boolean
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: number): void
}>()


</script>

<template>
  <div :class="{error:error}" class="wrapper">
    <select :value="modelValue" class="s-select"
            @change="$emit('update:modelValue',$event.target.value)"
    >

      <option disabled selected>{{ placeholder }}</option>
      <option v-for="variant in data" :selected="modelValue?placeholder: modelValue==variant.value"
              :value="variant.value"
      >
        {{ variant.name }}
      </option>
    </select>
    <span v-show="error">Выберите значение</span>
  </div>

</template>

<style lang="scss" scoped>
.s-select {
  padding: 10px;
  font-family: Montserrat;
  font-size: 14px;
  font-weight: 400;
  line-height: 19px;
  letter-spacing: -0.0015em;
  text-align: left;
  color: #9292A0;
  outline: none;
  border-radius: 11px;
  border: 1px solid #E6E6EB;
  width: 100%;
  cursor: pointer;
}

.error {
  select {
    border-color: red;

  }

  span {
    color: red;
    bottom: -17px;
    font-family: Montserrat;
    font-size: 14px;
    position: absolute;
  }
}

.wrapper {
  position: relative;
  display: flex;

}
</style>