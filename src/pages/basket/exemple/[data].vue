<script setup lang="ts">
import FormBasket from '../../../components/FormBasket.vue'
import { useRoute } from 'vue-router/auto'
const route = useRoute('/basket/exemple/[data]')
</script>
<template>
  <FormBasket :data="JSON.parse(route.params.data)" />
</template>