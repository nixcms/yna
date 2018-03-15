<template>
  <div id="app">
    <header class="header title">
      <p class="title-text">ShoppingList</p>
    </header>
    <div class="container">
      <list :todos="todos"></list>
      <detail></detail>
    </div>
  </div>
</template>

<script>
  import 'normalize.css';
  import '@/assets/css/common.css';

  import data from './data.json';
  import List from './components/List';
  import Detail from './components/Detail';

  export default {
    name: 'App',
    components: {
      List,
      Detail,
    },
    data() {
      return {
        todos: data,
      };
    },
  };
</script>

<style scoped>
  .header {
    padding: 15px;
  }
  .title-text {
    font-size: 2em;
  }
  .container {
    margin: 150px auto 0;
    max-width: 800px;
    padding: 0 10px;
    display: flex;
    justify-content: space-between;
    align-items: stretch;
  }

  @media screen and (max-width: 800px) {
    .container {
      margin-top: 35px;
      flex-direction: column;
      align-items: center;
      justify-content: auto;
    }
    .title-text {
      text-align: center;
    }
  }
</style>
