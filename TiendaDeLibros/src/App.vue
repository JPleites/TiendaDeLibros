<script setup>
  import {ref, reactive, onMounted} from 'vue'
  import { db } from './data/libros'
  import libro from './components/libro.vue'
  import Header from './components/header.vue'
  import Footer from './components/footer.vue'

  const libros = ref ([])
  const carrito = ref [[]]
  const libro = ref ({})

  onMounted( () =>{
    libros.value = db;
    libro.value = db[3]
  })

  const agregaCarrito = (libro) => {
      const existeCarrito = carrito.value.findIndex(producto => producto.id === libro.id)
      if(existeCarrito >= 0) {
        carrito.value[existeCarrito].cantidad++
      }
      else{
        libro.cantidad = 1
        carrito.value.push(libro);
      }
  }

  const decrementarCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    if (carrito.value[index] <= 1) return 
    carrito.value[index].cantidad-- 
  }

  const incrementarCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    carrito.value[index].cantidad++    
  }

</script>

<template>
  <Header
  :carrito="carrito"
  :libro="libro"
  @decrementar-cantidad="decrementarCantidad"
  @incrementar-cantidad="incrementarCantidad"
  @agregar-carrito="agregaCarrito"/>

  <main class="container-xl mt-5">
    <h2>Nuestra Colección</h2>

    <div class="row mt-5">
      <libro 
        v-for:="libro in libros"
        :libro = "libro"
        @agregar-carrito="agregaCarrito"
      />
    </div>
  </main>

  <Footer/>
</template>

<style scoped>

</style>
