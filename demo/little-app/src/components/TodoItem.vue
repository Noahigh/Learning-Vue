<template>
  <li class="item">
    <input type="checkbox" v-model="checked">
    <!-- 插槽写法 - 具名插槽 -->
    <slot name="todoItem"></slot>
  </li>
</template>

<script>
export default {
  props: ['item'],
  data() {
    return {
      checked: false,
    }
  }
}
</script>

<style>
  .item {
    color: blueviolet;
  }
</style>