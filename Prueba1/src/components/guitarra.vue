<script setup>
    const props = defineProps({
        guitarra : {
            type: Object,
            required: true
        }
    })
</script>

<template>
    <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Coleccion</h2>

    <div class="row mt-5">
      <div v-for = "guitarra in guitarras" class="col-md-6 col-lg-4 my-4 row align-items-center">
        <div class="col-4">
          <img class="img-fluid" v-bind:src='/img/'+guitarra.Imagen alt="Imagen Guitarra">
        </div>
        <div class="col-8">
          <h3 class="text-black fs-4 fw-hold text-uppercase">Luckater</h3>
          <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Reprehenderit fuga quod quia consequatur totam, quas velit quaerat blanditiis error minima accusamus earum dolorum, eligendi alias optio non atque eveniet laborum?</p>
          <p class="fw-black text-primary f2-3">$299</p>
          <button type="button" class="btn btn-dark w-100">Agregar al carrito</button>
        </div>
      </div>
    </div>
    <!-- Fin guitarra -->
  </main>
</template>

<style>
</style>