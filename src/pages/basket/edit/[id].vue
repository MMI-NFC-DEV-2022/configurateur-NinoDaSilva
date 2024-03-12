<script setup lang="ts">
import FormBasket from "../../../components/FormBasketSupabase.vue";
import {useRoute} from "vue-router/auto"
const route = useRoute("/basket/edit/[id]")
</script>
<template>
  <FormBasket :id="route.params.id" />
</template>