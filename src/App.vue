<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <h1 class="text-4xl pb-2">Test Agence imo</h1>

    <nav class="pb-10 *:text-xl flex flex-col *:pt-1 menu">
      <RouterLink to="/" class="hover:text-green-900 hover:font-bold">Home</RouterLink>
      <RouterLink to="/FormPage" class="hover:text-green-900 hover:font-bold">Personnalisation</RouterLink>
      <RouterLink to="/basket/" class="hover:text-green-900 hover:font-bold">Listes des Baskets</RouterLink>
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
