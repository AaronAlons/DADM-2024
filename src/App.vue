<script setup>
import { ref } from 'vue';
const header = ref('App lista de compras');
</script>

<template>
    <h1>
    <!--agregamos un icono al codigo a un costado del header-->
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>
 
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
