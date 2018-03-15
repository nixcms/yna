<template>
  <div id="app">
    <header class="header title">
      <p class="title-text">ShoppingList</p>
    </header>
    <div class="container">
      <list :items="items"></list>
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
  import eventBus from './eventBus';

  export default {
    name: 'App',
    components: {
      List,
      Detail,
    },
    data() {
      return {
        items: data,
      };
    },
    methods: {
      getItemIndex(changedItem) {
        for (let i = 0; i < this.items.length; i += 1) {
          const item = this.items[i];

          if (item.id === changedItem.id) {
            return i;
          }
        }
      },
    },
    mounted() {
      eventBus.$on('CHANGE_ITEM', (newItem) => {
        const itemIndex = this.items.findIndex(el => (el.id === newItem.id));

        this.items.splice(itemIndex, 1, { ...newItem });
      });
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
