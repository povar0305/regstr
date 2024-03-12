<script lang="ts" setup>

</script>

<template>
  <button class="s-button">
    <slot/>
  </button>
</template>

<style lang="scss" scoped>
button {
  outline: none;
  border: none;
  width: 302px;
  border-radius: 8px;
  background: #497ADA33;
  padding-top: 11px;
  padding-bottom: 10px;
  display: flex;
  justify-content: center;
  cursor: pointer;
  transition: 0.3s;

  &:hover {
    background: rgba(73, 122, 218, 0.35);
  }
}
</style>