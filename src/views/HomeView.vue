<script setup lang="ts">
import { storeToRefs } from "pinia";
import { useUserStore } from "@/stores/user";

const { form } = storeToRefs(useUserStore());
</script>
<template>
  <div>
    <h1>Bienvenido, {{ form.user }}</h1>
  </div>
</template>

<style scoped> 

h1 {
  color: beige;
  font-size: 50px
}
</style>
