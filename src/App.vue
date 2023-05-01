<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
  
    <div class="wrapper">

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/recipie">My Recipe Book</RouterLink>
        <RouterLink to="/planner">Meal Planner</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
</style>
