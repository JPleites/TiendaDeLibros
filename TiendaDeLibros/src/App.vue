<script setup>
  import { ref, reactive, onMounted} from 'vue'
  import { db } from './data/libros.js'
  import Libro from './components/Libro.vue'
  import Header from './components/Header.vue'
  import Footer from './components/Footer.vue'

  const libros = ref([])
  const carrito = ref([])
  const libro = ref({})

  onMounted( () =>{
    libros.value = db;
    libro.value = db[3];
  })

  const agregarCarrito = (libro) =>{

    const existeCarrito = carrito.value.findIndex(producto => producto.id === libro.id)
    
    if(existeCarrito >= 0){
      carrito.value[existeCarrito].cantidad++
    }else{
      libro.cantidad = 1
      carrito.value.push(libro);
    }
  }

  const decrementarCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    if(carrito.value[index].cantidad <= 1) return 
    carrito.value[index].cantidad--
  }

  const incrementarCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    carrito.value[index].cantidad++
  }

  const eliminarProducto = (id) => {
    carrito.value = carrito.value.filter(producto => producto.id !== id)
  }

  const vaciarCarrito = () => {
    carrito.value = []
  }
</script>

<template>
  <!--Renderizacion del Header-->
  <Header 
    :carrito="carrito"
    :libro="libro"
    @decrementar-cantidad="decrementarCantidad"
    @incrementar-cantidad="incrementarCantidad"
    @agregar-carrito="agregarCarrito"
    @eliminar-producto="eliminarProducto"
    @vaciar-carrito="vaciarCarrito"
  />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <!--Renderizacion-->
      <Libro 
            v-for="libro in libros"
           :libro = "libro" 
           @agregar-carrito="agregarCarrito"
        />
        </div>
  </main>

  <!--Renderizacion del Footer-->
  <Footer/>
  
</template>

<style scoped>
  h1{
    text-transform: uppercase;
    color: rgb(23, 14, 78);
  }

</style>
