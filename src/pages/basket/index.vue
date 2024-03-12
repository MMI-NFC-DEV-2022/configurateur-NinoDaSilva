<script setup lang="ts">
import { supabase } from '@/supabase'
import BasketProfil from '@/components/SvgProfil.vue'

const { data: listeBasket, error } = await supabase.from('Basket').select('*')
if (error) console.log("N'a pas pu charger la table Basket :", error)

</script>

<template>
  <section>
    <h1 class="text-2xl">Liste de Baskets</h1>
    <ul class="flex flex-wrap gap-2">
      <li class="w-64" v-for="uneBasket in listeBasket" :key="uneBasket.id">
        <RouterLink :to="{
            name: '/basket/edit/[id]',
            params: { id: uneBasket.id }
          }"
        >
          <BasketProfil class="w-64" v-bind="uneBasket" />
        </RouterLink>
      </li>
    </ul>
  </section>
</template>
