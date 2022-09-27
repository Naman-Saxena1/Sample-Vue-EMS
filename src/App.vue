<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
    
  <nav>
    <RouterLink to="/">Register</RouterLink>
    <RouterLink to="/records">Records</RouterLink>
  </nav>

  <RouterView />
</template>

<style scoped>
nav{
  width: 100%;
  font-size: 2rem;
  display: flex;
  padding: 1rem 0;
  justify-content: space-evenly;
  border-bottom: 2px solid var(--color-cadetblue);
}

nav a{
  padding: 1rem 3rem;
  color: var(--color-light-green);
  border-radius: 4rem;
}

nav a:hover{
  background-color: var(--color-hover);
}

nav a.router-link-active, nav a.router-link-exact-active{
  color: var(--color-white);
  background-color: var(--color-cadetblue);
}
</style>