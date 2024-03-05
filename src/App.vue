<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <h1 class="text-4xl pb-2">Test Agence imo</h1>

    <nav class="pb-10 *:text-red-500 *:text-xl flex flex-col *:pt-1 menu">
      <RouterLink to="/">Home</RouterLink>
    </nav>
  </header>

  <main>
    <Suspense>
      <RouterView />
    </Suspense>
  </main>

  <footer>
    
  </footer>
</template>
