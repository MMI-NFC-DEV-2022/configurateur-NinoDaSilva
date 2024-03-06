<script setup lang="ts">
import { ref } from 'vue'
import { type Basket, colors, materiaux } from '@/types'
import SvgProfil from '@/components/SvgProfil.vue'
import SvgDessus from '@/components/SvgDessus.vue'
import FormListColor from './FormListColor.vue'

const props = defineProps<{
  data?: Basket
  id?: string
}>()

const basket = ref<Basket>(props.data ?? {})
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
      <FormListColor name="semelle" label="semelle" />
      <FormListColor name="empeigne" label="empeigne" />
      <FormListColor name="pointe" label="pointe" />
      <FormListColor name="oeillet" label="oeillet" />
      <FormListColor name="bande" label="bande" />
      <FormListColor name="languette" label="languette" />
      <FormListColor name="lacet" label="lacet" />
      <FormListColor name="trimestre" label="trimestre" />
      <!-- Matériaux -->
      <FormKit
        name="materiaux"
        label="materiaux"
        value="#ffffff"
        type="radio"
        :options="materiaux"
        :sections-schema="{ inner: { $el: null }, decorator: { $el: null } }"
        input-class="peer sr-only"
        options-class="flex gap-2"
      >
        <template #label="context">
          <div class="h-6 w-6 rounded-full border-2 peer-checked:border-red-600" :style="{ backgroundImage: `url(${context.option.value})` }" />
          <span class="sr-only">{{ context.option.label }}</span>
        </template>
      </FormKit>
    </FormKit>
  </div>
</template>
