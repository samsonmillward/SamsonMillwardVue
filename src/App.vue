<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import OverviewComponent from './components/OverviewComponent.vue'
</script>

<template>
  <div class="wrapper">
    <OverviewComponent />

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/work-history">Work History</RouterLink>
    </nav>
    <RouterView />
  </div>

</template>

<style scoped></style>
