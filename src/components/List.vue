<template>
  <div class="list">
    <div class="title">
      <p class="title-text">Add your items hear</p>
    </div>
    <ul class="shoping-list">
      <li
        v-for="item in items"
        :key="item.id"
        :item="item"
        :currentItemId="currentItemId"
        is="item"
      >
      </li>
      <li>
        <a
          class="add-item"
          @click="addNewItem()"
        >
          Add item
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
  import eventBus from '../eventBus';
  import Item from './Item';

  export default {
    name: 'List',
    props: ['currentItemId', 'items'],
    components: {
      Item,
    },

    data() {
      return {

      };
    },

    methods: {
      addNewItem() {
        eventBus.$emit('ADD_NEW_ITEM');
      },
    },
  };
</script>

<style scoped>
  .list {
    border: 1px solid #d3d3d3;
    width: 300px;
  }
  .title-text {
    padding: 10px;
    text-transform: uppercase;
  }
  .shoping-list li {
    padding: 10px;
    list-style-type: none;
    border-bottom: 1px solid #d3d3d3;
    line-height: 1;
  }
  .add-item {
    padding-left: 21px;
    cursor: pointer;
  }
  .add-item:hover {
    color: #333;
  }
  @media screen and (max-width: 800px) {
    .list {
      margin-bottom: 25px;
    }
  }
</style>
