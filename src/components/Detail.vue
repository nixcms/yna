<template>
  <div class="detail">
    <div class="title">
      <p class="title-text">{{item.title}} detail</p>
    </div>
    <form class="form">
      <div class="form-row">
        <label for="">Quantity</label>
        <input
          type="number"
          v-model="changedItem.quantity"
          @blur="changeItem()"
        >
      </div>
      <div class="form-row">
        <label for="">Price</label>
        <input
          type="number"
          v-model="changedItem.price"
          @blur="changeItem()"
        >
      </div>
      <div class="form-row">
        <label for="">Description</label>
        <textarea
          v-model="changedItem.description"
          @blur="changeItem()"
        >
        </textarea>
      </div>
    </form>
  </div>
</template>

<script>
  import eventBus from '../eventBus';

  export default {
    name: 'Detail',
    props: ['item'],

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

    methods: {
      changeItem() {
        eventBus.$emit('CHANGE_ITEM', this.changedItem);
      },
    },

    filters: {
      onlyNumbers(value) {
        let newValue = value;

        if (newValue.match(/[^0-9]/g)) {
            newValue = newValue.replace(/[^0-9]/g, '');
        }

        return newValue;
      },
    },
  };
</script>

<style scoped>
  .detail {
    border: 1px solid #d3d3d3;
    width: 100%;
    max-width: 465px;
  }
  .title-text {
    padding: 10px;
    text-transform: uppercase;
  }
  .form {
    padding: 10px 10px 50px 10px;
  }
  .form-row {
    margin-bottom: 20px;
  }
  label {
    display: block;
    margin-bottom: 2px;
    color: #333;
  }
  input,
  textarea {
    display: block;
    width: 100%;
    border: 1px solid #d3d3d3;
    padding: 5px;
    font-size: 14px;
    color: #999;
  }
  input:focus,
  textarea:focus {
    color: #000;
    border-color: #000;
    outline: none;
  }
  textarea {
    resize: vertical;
    min-height: 70px;
  }
  @media screen and (max-width: 800px) {
    .detail {
      width: 300px;
    }
  }
</style>
