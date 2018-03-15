<template>
  <li class="item">
    <input
      type="checkbox"
      class="checkbox"
      v-model="item.done"
    />
    {{ item.title }}
    <a class="close"></a>
  </li>
</template>

<script>
  export default {
    name: 'Item',
    props: ['item'],
  };
</script>

<style scoped>
  .item {
    display: flex;
    align-items: center;
  }
  .item.active {
    border: 1px solid #000;
  }
  .checkbox {
    margin-right: 4px;
  }
  .close {
    margin-left: auto;
    width: 12px;
    height: 12px;
    background: url(../assets/images/close.png) no-repeat 0 0;
    background-size: contain;
    cursor: pointer;
  }
</style>
