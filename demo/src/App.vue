<template>
  <router-view />
</template>

<script>
console.log(import.meta.env);
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'App'
})
</script>
