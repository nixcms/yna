<template>
  <div id="app">

    <!-- navbar -->
    <navbar></navbar>

    <!-- content -->
    <div class="container-fluid">
      <div class="row">
        <div class="container">
          <itemList></itemList>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import navbar from './components/navbar.vue'
import itemList from './components/itemList.vue'
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    navbar,
    itemList
  }
}
</script>

<style>
  * {
      -webkit-box-sizing: border-box;
      -moz-box-sizing: border-box;
      box-sizing: border-box;
  }

  body {
      font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
      font-size: 14px;
      line-height: 1.42857143;
      color: #000;
      background-color: #fff;
  }

  .container-fluid::before,
  .container-fluid::after,
  .container::before,
  .container::after,
  .row:before,
  .row:after,
  .navbar:before,
  .navbar:after {
      content: " ";
      display: table;
  }

  .container-fluid::before,
  .container-fluid::after,
  .container::before,
  .container::after,
  .row:before,
  .row:after,
  .navbar:before,
  .navbar:after {
      content: " ";
      display: table;
      clear: both;
  }

  .container-fluid {
      padding-right: 15px;
      padding-left: 15px;
      margin-right: auto;
      margin-left: auto;
  }

  .container {
      width: 100%;
      max-width: 800px;
      padding-right: 15px;
      padding-left: 15px;
      margin-right: auto;
      margin-left: auto;
  }

  .row {
      margin-right: -15px;
      margin-left: -15px;
  }

</style>
