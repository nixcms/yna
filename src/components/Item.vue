<template>
  <li :class="['item', itemClasses]">
    <input
      type="checkbox"
      class="checkbox"
      v-model="changedItem.done"
      v-on:change="changeItem()"
    />
    <input
      type="text"
      placeholder="Enter the name"
      class="product-name"
      v-model="changedItem.title"
      @blur="changeItem()"
      @focus="initEditing()"
    />
    <a
      class="close"
      @click="deleteItem()"
    >
    </a>
  </li>
</template>

<script>
  import eventBus from '../eventBus';

  export default {
    name: 'Item',
    props: ['currentItemId', 'item'],

    data() {
      return {
        changedItem: Object.assign({}, this.item),
      };
    },

    watch: {
      item(value) {
        this.changedItem = Object.assign({}, value);
      },
    },

    computed: {
      itemClasses() {
        return {
          done: this.item.done,
          active: (this.currentItemId === this.item.id),
        };
      },
    },

    methods: {
      changeItem() {
        eventBus.$emit('CHANGE_ITEM', this.changedItem);
      },

      initEditing() {
        eventBus.$emit('INIT_EDITING', this.item.id);
      },

      deleteItem() {
        eventBus.$emit('DELETE_ITEM', this.item.id);
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
    border-bottom: 2px solid #999;
  }
  .checkbox {
    margin-right: 4px;
  }
  .product-name {
    flex-grow: 1;
    border: none;
    padding: 10px;
    background: transparent;
    outline: none;
    color: #999;
  }
  .product-name::placeholder {
    opacity: .2;
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
