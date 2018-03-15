<template>
  <li :class="['item', {'done': item.done}]">
    <input
      type="checkbox"
      class="checkbox"
      v-model="changedItem.done"
      v-on:change="changeItem()"
    />
    <input
      type="text"
      class="product-name"
      v-model="changedItem.title"
      v-on:blur="changeItem()"
    />
    <a class="close"></a>
  </li>
</template>

<script>
  import eventBus from '../eventBus';

  export default {
    name: 'Item',
    props: ['item'],
    data() {
      return {
        changedItem: Object.assign({}, this.item),
      };
    },
    methods: {
      changeItem() {
        eventBus.$emit('CHANGE_ITEM', this.changedItem);
      },
    },
  };
</script>

<style scoped>
.item {
  display: flex;
  align-items: center;
}
.item.done {
  text-decoration: line-through;
}
.item.active {
  border: 1px solid #000;
}
.checkbox {
  margin-right: 4px;
}
.product-name {
  border: none;
  background: transparent;
  outline: none;
  color: #999;
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
