<script setup lang="ts">
import { ref } from 'vue'
import { supabase } from '@/supabase'
import { type Basket, materiaux } from '@/types'
import { useRouter, useRoute } from 'vue-router'
import SvgProfil from '@/components/SvgProfil.vue'
import SvgDessus from '@/components/SvgDessus.vue'
import FormListColor from './FormListColor.vue'

// const props = defineProps<{
//   data?: Basket
//   id?: string
// }>()

// const basket = ref<Basket>(props.data ?? {})
const basket = ref({});

const router = useRouter();
// Envoie des donnees du formulaire
async function upsertBasket(dataForm, node) {
    const { data, error } = await supabase.from("Basket").upsert(dataForm).select();
    if (error) node.setErrors([error.message]);
    else {
        node.setErrors([]);
        router.push({name: "/basket/edit/[id]", params: {id: data[0].id} });
    }
}

// Redirection vers le quartier de modifiee
const route = useRoute("/basket/edit/[id]");
if (route.params.id) {
    let { data, error } = await supabase.from("Basket").select("*").eq("id", route.params.id);
    if (error) console.log("error", error);
    else basket.value = (data as any[]) [0];
}
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

    <FormKit type="form" v-model="basket" @submit="upsertBasket"
      :config="{
        classes: {
          input: 'p-1 rounded border-gray-300 shadow-sm border',
          label: 'text-gray-600'
        }
      }"
      :submit-attrs="{ classes: { input: 'bg-red-300 p-1 rounded' } }"
    >
      <FormListColor name="semelle_color" label="semelle" />
      <FormListColor name="empeigne_color" label="empeigne" />
      <FormListColor name="pointe_color" label="pointe" />
      <FormListColor name="oeillet_color" label="oeillet" />
      <FormListColor name="bande_color" label="bande" />
      <FormListColor name="languette_color" label="languette" />
      <FormListColor name="lacet_color" label="lacet" />
      <FormListColor name="trimestre_color" label="trimestre" />
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
          <div
            class="h-6 w-6 rounded-full border-2 peer-checked:border-red-600"
            :style="{ backgroundImage: `url(${context.option.value})` }"
          />
          <span class="sr-only">{{ context.option.label }}</span>
        </template>
      </FormKit>
    </FormKit>
  </div>
</template>
