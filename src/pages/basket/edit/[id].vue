<script setup lang="ts">
import FormSvg from "../../../components/FormBasket.vue";
import {useRoute} from "vue-router/auto"
const route = useRoute("/basket/edit/[id]")
</script>
<template>
  <FormSvg :id="route.params.id" />
</template>