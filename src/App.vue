<script setup>
import { ref } from 'vue';
const header = ref('App lista de compras');
const items = ref([
    {id:'1', label:'10 bolillos'},
    {id:'2',label:'1 lata de frijoles'},
    {id:'3',label:'1 chela'},
    {id:'4',label:'1 nutella'},
    {id:'5',label:'1 lata de atun'},
    {id:'6',label:'1 pc gamer'}
]);
const newItem =ref('');
const newItemHighPriority = ref(false);
/*Helados
const iceCreamFlavors = ref([]);*/
/*Enlazado con checkboxes
const newItemHighPriority = ref(false);*/
/*radio buttons
const newItemPriority= ref('low');
*/
</script>

<template>
    <h1>
    <!--agregamos un icono al codigo a un costado del header-->
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1> 
<!--<input v-model="newItem"
type="text" 
placeholder="Agregar articulo">
-->
<!--Radio Buttons
<label>
    <input type="radio" value="low" v-model="newItemPriority">
    Bajo
</label>
<label>
    <input type="radio" value="high" v-model="newItemPriority">
    Alto
</label>
{{ newItemPriority =='low'?'🦖':'❤️‍🔥'}}
-->
<!--Enlazado con checkboxes
Radio Buttons 
<label><input type="checkbox" v-model="newItemHighPriority">Alta Prioridad</label> <br>
{{ newItemHighPriority }}-->
<!-- Helados
<label>
		<input type="checkbox" v-model="iceCreamFlavors" value="vanilla">
		Vanilla
	</label>
  <label>
		<input type="checkbox" v-model="iceCreamFlavors" value="chocolate">
		Chocolate
	</label>
  <label>
		<input type="checkbox" v-model="iceCreamFlavors" value="strawnerry">
		Strawberry
	</label>
  {{iceCreamFlavors}}
-->
<!--agregar sin guardar
<input 
      type="text" 
      placeholder="Add Item" 
      v-on:keyup.enter="items.push({id: items.length + 1, label: newItem})" 
      v-model.trim="newItem">
 Caja de seleccion de prioridad 
<label>
    <input type="checkbox" v-model="newItemHighPriority">
    High Priority
  </label>
   Boton 
<button 
  class="btn btn-primary" 
  v-on:click="items.push({id: items.length + 1, label: newItem})">
  Salvar Articulo
</button>
-->

<!-- Agrupando en un div las entradas -->
<form v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item fomr">
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      alta prioridad
    </label>
    <!-- Boton -->
    <button
      class="btn btn-primary"
    >
      GUARDAR PRODUCTO
    </button>
  </form>
<!--ul>li*3 es el lenguaje emet a usar-->
<ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🦖':'🛒'}} {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
button{
    background-color: blue;
}
</style>
