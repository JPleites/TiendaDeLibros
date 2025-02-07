<script setup>
    const props = defineProps({
        carrito: {
            type: Array,
            required: true,
        }
    })

    defineEmits('decrementar-cantidad','incrementar-cantidad')

</script>

<template>
    <header class="py-5 header">
        <div class="container-xl">
            <div class="row justify-content-center justify-content-md-between">
                <div class="col-8 col-md-3">
                    <a href="index.html">
                        <img class="img-fluid" src="/img/logo.png" width="100px">
                    </a>
                </div>
                <nav class="col-md-6 a mt-5 d-flex align-items-start justify-content-space-between">
                    <div class="carrito">
                        <img class="img-fluid" src="/img/carrito.png" width="100px" height="100px">
                        <div id="carrito" class="bg-white p-3">
                            <p v-if="carrito.length === 0" class="text-center m-0">El carrito está vacio</p>
                            <div v-else>
                                <table class="w-100 table">
                                    <thead>
                                        <tr>
                                            <th>Imagen</th>
                                            <th>Titulo</th>
                                            <th>Precio</th>
                                            <th>Cantidad</th>
                                            <th></th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr 
                                            v-for="producto in carrito"
                                        >
                                            <td>
                                                <img class="img-fluid"
                                                :src="'/img'+ producto.imagen + '.jpg'">
                                            </td>
                                            <td>
                                                {{ producto.titulo }}
                                            </td>
                                            <td class="fw-bold">
                                                Lps. {{ producto.precio }}
                                            </td>
                                            
                                        </tr>
                                        <tr>
                                            <td class="flex align-items-start gap-4">
                                                <button type="button" class="btn btn-dark" 
                                                @click="$emit('decrementar-cantidad', producto.id)">
                                                    -
                                                </button>
                                                {{ producto.cantidad }}
                                                <button type="button" class="btn btn-dark"
                                                @click="$emit('incrementar-cantidad', producto.id)">
                                                    +
                                                </button>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </nav>
            </div>
        </div>
    </header>
</template>

<style>
</style>