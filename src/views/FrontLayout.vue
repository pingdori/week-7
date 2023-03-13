<template>
    這是前台頁面
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">寶可夢圖鑑屋</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link to="/" class="nav-link" aria-current="page" >Home</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/about" class="nav-link" >About</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/products" class="nav-link" >產品列表</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/cart" class="nav-link" >購物車</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/admin/products" class="nav-link" >後台產品列表</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>
    <hr/>
    <RouterView></RouterView>
</template>

<script>
import { RouterView } from 'vue-router'
export default {
  components: {
    RouterView
  }
}
</script>
