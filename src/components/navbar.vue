<template>
  <nav class="navbar custom-navbar">
      <div class="navbar-header">
          <a href="#" class="logo navbar-brand">ShoppingList</a>
      </div>
  </nav>
</template>

<style>
  .navbar {
      position: relative;
      min-height: 50px;
      padding: 15px;
      background: linear-gradient(to right, #00e591, #2fefbc);
  }

  .navbar-header {
      float: left;
  }

  .logo {
      font-size: 2em;
      line-height: 20px;
      color: #fff;
      float: left;
      height: 50px;
      padding: 15px 15px;
      text-decoration: none;
  }
  @media screen and (max-width: 768px) {
    .logo, .navbar-header {
      float: none;
      text-align: center;
    }
  }
</style>
