<script setup>
  import { ref, reactive, onMounted} from 'vue'
  import { db } from './data/guitarra'
  import guitarra from './components/guitarra.vue';

  const guitarra = ref([])
  onMounted( () => {
    guitarra.value = db;
  })
</script>

<template>
  
</template>

<style scoped>
  
</style>
