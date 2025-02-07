<script setup>
    const props = defineProps({
        libro:{
            type: Object,
            required: true,
        }
    })

    defineEmits(['agregar-carrito'])
</script>

<template>
    <div class="col-md-6 col-lg-4 row align-items-center">
        <div class="col-4">
          <img 
          class="img-fluid" 
          v-bind:src="'/img/'+libro.imagen+'.jpg'">
        </div>
        <div class="col-8">
          <h3 class="text-black fs-4 fw-bold text-uppercase">{{libro.titulo}}</h3>
          <p>{{ libro.descripcion }}</p>
          <p><b>Autor: </b>{{ libro.autor }}</p>
          <p><b>Editorial: </b>{{ libro.editorial }}</p>
          <p class="fw-black text-primary fs-3">Lps {{libro.precio}}</p>
          <button type="button" 
            class="btn btn-dark w-100" 
            @click="$emit('agregar-carrito', libro)">
            Agregar al Carrito
          </button>
        </div>
    </div>
</template>

<style>

</style>