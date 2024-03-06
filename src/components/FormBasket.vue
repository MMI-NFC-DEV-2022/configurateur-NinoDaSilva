<script setup lang="ts">
import { ref } from 'vue'
import { type Basket, colors } from '@/types'
import SvgProfil from '@/components/SvgProfil.vue'
import SvgDessus from '@/components/SvgDessus.vue'

const props = defineProps<{
  data?: Basket;
  id?: string;
}>();

const basket = ref<Basket>(props.data ?? {});
</script>

<template>
  <div class="p-2">
    <ul class="flex gap-1">
      <li><a href="#profil">Profil</a></li>
      <li><a href="#dessus">Dessus</a></li>
    </ul>
    <div class="carousel w-64">
      <SvgProfil class="carousel-item w-64" v-bind="basket" id="profil"></SvgProfil>
      <SvgDessus class="carousel-item w-64" v-bind="basket" id="dessus"></SvgDessus>
    </div>

    <FormKit type="form" v-model="basket">
      <FormKit name="semelle" label="semelle" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="empeigne" label="empeigne" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="pointe" label="pointe" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="oeillet" label="oeillet" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="bande" label="bande" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="languette" label="languette" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="lacet" label="lacet" value="#ffffff" type="select" :options="colors"/>
      <FormKit name="trimestre" label="trimestre" value="#ffffff" type="select" :options="colors"/>
    </FormKit>
  </div>
</template>
