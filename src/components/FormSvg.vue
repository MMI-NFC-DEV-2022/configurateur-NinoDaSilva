<script setup lang="ts">
import { ref } from 'vue'
import type { ChaussureSvg } from '@/types-svg'
import SvgProfil from '@/components/SvgProfil.vue'
import SvgDessus from '@/components/SvgDessus.vue'
const chaussure = ref<ChaussureSvg>({})
</script>

<template>
  <div class="p-2">
    <ul class="flex gap-1">
      <li><a href="#profil">Profil</a></li>
      <li><a href="#dessus">Dessus</a></li>
    </ul>
    <div class="carousel w-64">
      <SvgProfil class="carousel-item w-64" v-bind="chaussure" id="profil"></SvgProfil>
      <SvgDessus class="carousel-item w-64" v-bind="chaussure" id="dessus"></SvgDessus>
    </div>

    <FormKit type="form" v-model="chaussure">
      <FormKit name="semelle" label="semelle" value="#ffffff" type="color"/>
      <FormKit name="empeigne" label="empeigne" value="#ffffff" type="color"/>
      <FormKit name="pointe" label="pointe" value="#ffffff" type="color"/>
      <FormKit name="oeillet" label="oeillet" value="#ffffff" type="color"/>
      <FormKit name="bande" label="bande" value="#ffffff" type="color"/>
      <FormKit name="languette" label="languette" value="#ffffff" type="color"/>
      <FormKit name="lacet" label="lacet" value="#ffffff" type="color"/>
      <FormKit name="trimestre" label="trimestre" value="#ffffff" type="color"/>
    </FormKit>
  </div>
</template>
