<template>
  <li class="item">
    <input type="checkbox" v-model="checked">
    <!-- 插槽写法 - 具名插槽 -->
    <slot name="todoItem" v-bind="{checked}"></slot>
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

<!-- 局部样式，不会污染全局样式 -->
<style scoped>
</style>

<style>
  .item {
    color: blueviolet;
  }
</style>