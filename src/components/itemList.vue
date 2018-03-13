<template>
  <div id="listIt">
    <div class="starter-template">
      <div class="shoppingList">
        <div class="shoppingList__Head">
          <h3>Add your item hear</h3>
        </div>
        <div class="shoppingList__Body">
          <ul v-if="items.length">
            <li
              v-for="item in items"
              :class="{ 'removed': item.checked }"
              :key="item.id"
              :item="item"
  		        @remove="removeItem(idToRemove)"
            >
              <div class="itemField">
                <input type="checkbox" v-model="item.checked">
                <input type="text" v-model="item.text" @click="handleItemClick(item)" class="itemFieldText">
              </div>
              <button @click="removeItem(item.id)">
                X
              </button>
            </li>
          </ul>
          <p v-else>
            Nothing left in the list. Add a new item in the input above.
          </p>

          <input v-model="newItem" @keyup.enter="addItem" placeholder="Add item" type="text" class="addItemInput">

        </div>
      </div>
      <div class="shoppingDetails" v-show="isEditing && items.length">
        <div class="shoppingList__Head">
          <h3><span>{{activeItem.text}}</span> details</h3>
        </div>
        <div class="shoppingList__Body">
          <div class="form-control">
            <label>Quantity</label>
            <input type="text" :value="activeItem.quantity" @change="handleQuantityChange($event)">
          </div>
          <div class="form-control">
            <label>Price</label>
            <input type="text" :value="activeItem.price" @change="handlePriceChange($event)">
          </div>
          <div class="form-control">
            <label>Description</label>
            <textarea rows="4" cols="40" :value="activeItem.description" @change="handleDescriptionChange($event)"></textarea>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
var data = {
  items: [
    {
      text: 'Milk',
      checked: true,
      id: Math.floor(Math.random() * 100),
      quantity: '1',
      price: '25',
      description: ''
    },
    {
      text: 'Bread',
      checked: false,
      id: Math.floor(Math.random() * 100),
      quantity: '3',
      price: '10',
      description: ''
    },
    {
      text: 'Cheerios',
      checked: false,
      id: Math.floor(Math.random() * 100),
      quantity: '7',
      price: '20',
      description: 'lorem'
    }
  ],
  newItem: '',
  isEditing: false,
  activeItem: {},
};

export default {
    name: 'listIt',
    data: function(){
      return data;
    },
    methods: {
      addItem: function () {
        var text;

        text = this.newItem.trim();
        if (text) {
          this.items.push({
            text: text,
            checked: false,
            id: Math.floor(Math.random() * 100),
            quantity: '',
            price: '',
            description: ''
          });
          this.newItem = '';
        }
      },
      removeItem (idToRemove) {
        this.items = this.items.filter(item => {
          return item.id !== idToRemove
        })
      },
      handleItemClick: function (item) {
        this.isEditing = true;
        this.activeItem = item;
      },
      handleQuantityChange: function (e) {
        var activeItem = this.items.find(item => item.id == this.activeItem.id);
        activeItem.quantity = e.target.value;
      },
      handlePriceChange: function (e) {
        var activeItem = this.items.find(item => item.id == this.activeItem.id);
        activeItem.price = e.target.value;
      },
      handleDescriptionChange: function (e) {
        var activeItem = this.items.find(item => item.id == this.activeItem.id);
        activeItem.description = e.target.value;
      }
    }
  };
</script>



<style>
  .starter-template {
    padding: 50px 0 40px;
  }

  .shoppingList {
    display: inline-block;
    width: 300px;
    vertical-align: top;
  }
  .shoppingList input[type="text"] {
    /* border: 0; */
  }
  .shoppingDetails {
    display: inline-block;
    width: 400px;
    vertical-align: top;
  }
  /* .shoppingDetails {
    display: none;
  } */
  .show {
    display: inline-block;
  }
  .shoppingList,
  .shoppingDetails {
    margin: 0 3px;
  }
  .shoppingDetails .shoppingList__Body {
    padding: 5px 5px;
  }
  .shoppingList__Head {
    background: linear-gradient(to right, #00e591, #2fefbc);
    padding: 5px 10px;
  }
  .shoppingList__Head h3 {
    font-size: 18px;
    color: #ffffff;
    font-weight: 400;
    margin: 0;
    text-transform: uppercase;
  }
  .shoppingList__Body {
    border: 1px solid #d3d3d3;
    min-height: 300px;
  }
  .shoppingList__Body p {
    color: #464646;
    padding: 0 5px;
    text-align: center;
  }
  .shoppingList__Body ul {
    list-style: none;
    padding-left: 0;
    margin: 0;
  }
  .shoppingList__Body ul li {
      color: #999;
    border-bottom: 1px solid #d3d3d3;
    padding: 5px 10px;
  }
  .addItemInput {
    width: 100%;
    padding: 8px 10px;
    margin-top: -1px;
    border: none;
    border-top: 1px solid #d3d3d3;
    padding-left: 29px;
  }
  input[type="checkbox"] {
    margin-right: 3px;
    width: 15px;
  }
  button {
    display: none;
  }
  .removed button {
    display: block;
  }
  .removed input[type="text"] {
    text-decoration: line-through;
  }
  .itemField {
    display: inline-block;
    width: calc(100% - 25px);
  }
  .itemField input[type="text"] {
    display: inline-block;
    width: calc(100% - 23px);
    outline: none;
    border: 0;
  }
  button {
    color: red;
    border: none;
    background: transparent !important;
    float: right;
    cursor: pointer;
    width: 20px;
  }
  button:hover {
    opacity: 0.8;
  }
  .form-control {
    margin-bottom: 8px;
  }
  .form-control label {
    display: block;
    color: #383838;
  }
  .form-control input {
    width: 100%;
  }
  .form-control textarea {
    box-shadow: none;
    border: 1px solid #d3d3d3;
    width: 100%;
    resize: vertical;
  }

  @media screen and (max-width: 768px) {
    .starter-template {
      max-width: 400px;
      margin: 0 auto;
    }
    .shoppingList, .shoppingDetails {
      width: 100%;
      margin: 0;
    }
    .shoppingList__Body {
      min-height: inherit;
    }
    .shoppingList {
      margin-bottom: 20px;
    }
  }
</style>
