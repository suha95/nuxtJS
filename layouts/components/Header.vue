<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container">
      <NuxtLink class="navbar-brand" to="/">Navbar</NuxtLink>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <NuxtLink class="nav-link" to="/">Ana Sayfa</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink class="nav-link" to="/content/NewContent">İçerik Ekle</NuxtLink>
          </li>
          <li class="nav-item">
            <NuxtLink class="nav-link" to="/content/ListContent">İçerikleri Listele</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style>
</style>