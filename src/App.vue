<script setup>

</script>

<template>
  <header >
    <!-- NAVIGATION BAR -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/">
          <img src="./assets/logo.svg" alt="" height="40" class="d-inline-block align-text-center">
          PokeVite
        </router-link>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/about">about</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <!-- CONTENT -->
    <router-view></router-view>
  <!-- -->

  <!-- FOOTER -->
    <footer class="bg-primary text-light">
      <div class="d-flex">
        {{ new Date().getFullYear() }} <p class="ms-3"> eduardo santos</p>
      </div>
    </footer>
  <!-- -->
  

  
</template>



<style>
body{
  height: 100vh;
  background-color: #00a0fd;
  background-image: linear-gradient(160deg, #024870 0%, #058b7c 100%);
}

footer{
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items:center;
  justify-content: center;
  height: 56px;
}
</style>