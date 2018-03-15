<template>
  <div class="list">
    <div class="title">
      <p class="title-text">Add your items hear</p>
    </div>
    <ul class="shoping-list">
      <li
        v-for="item in todos"
        :key="item.id"
        :item="item"
        is="item"
      >
      </li>
      <li>
        <a class="add-item">Add item</a>
      </li>
    </ul>
  </div>
</template>

<script>
  import Item from './Item';

  export default {
    name: 'List',
    components: {
      Item,
    },
    props: ['todos'],
    data() {
      return {

      };
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
    color: #999;
    line-height: 1;
  }
  .add-item {
    padding-left: 17px;
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
