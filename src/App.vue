<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";

import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"

</script>

<template>
  <div class="h-100 page-container">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Enterprise Bubbles</a>
  
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
  
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <RouterLink class="nav-link" to="/">Graph</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/about">About</RouterLink>
            </li>
  
            <li class="nav-item">
              <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
            </li>
  
          </ul>
          <form class="d-flex">
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success" type="submit">Filter</button>
          </form>
        </div>
      </div>
    </nav>
  
    <RouterView class="page-content page-container"/>
  </div>
</template>

<style scoped>
.h-100 {
    min-height: 100vh;
}
.flex-fill {
  flex:1 1 auto;
}
.container {
  display: flex;
  align-items: stretch;
}

.page-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: stretch;
}

.page-content {
  flex-shrink: 0;
  flex: auto;
}

</style>
