<script setup>
</script>

<template>



<nav class="navbar navbar-expand-lg navbar-dark fixed-top" style="background-color:#006d77">
  <div class="container-fluid">
    <a class="navbar-brand fw-bold" href="#"> <img src="icone/stock-market.png" width="30" height="30" alt="">StockExApp</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item">
          <nuxt-link to="/" class=""><a class="nav-link">Home</a>
         
        </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/stock" class=""><a class="nav-link">Stock</a>
         
        </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link to="/crypto" class=""><a class="nav-link">
         Crypto
       </a> </nuxt-link>
        </li>
        <li class="nav-item">
          <a class="nav-link ">Contact</a>
        </li>
      </ul>
    </div>
  </div>
</nav>

</template>

<style>
a:link {
  text-decoration: none;
  color: black !important;
}
</style>