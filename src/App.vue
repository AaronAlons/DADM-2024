<script setup>
import { ref } from 'vue';
//models
const header = ref('App lista de compras');
//items
//item model
const items = ref([
    {id:'1', label:'10 bolillos',purchased:true,priority:true},
    {id:'2',label:'1 lata de frijoles',purchased:false, priority:true},
    {id:'3',label:'1 chela',purchased:false, priority:true},
    {id:'4',label:'1 nutella',purchased:false, priority:true},
    {id:'5',label:'1 lata de atun', purchased:false,  priority:true},
    {id:'6',label:'1 pc gamer', purchased:false,  priority:true}
]);
//items method
const saveItem = () =>{
  items.value.push({id: items.value.length +1, label: newItem.value});
  //clean the input
  newItem.value='';
}

const newItem =ref('');
const newItemHighPriority = ref(false);
//visualizacion de formulario
const editing = ref(true);
const activateEdition =(activate) =>{
  editing.value=activate;
}
const link = () => {
  if (newItem.value.length === 0) {
    return 'https://google.com';
  }
  return `https://${newItem.value}`;
};

/*Helados
const iceCreamFlavors = ref([]);*/
/*Enlazado con checkboxes
const newItemHighPriority = ref(false);*/
/*radio buttons
const newItemPriority= ref('low');
*/
</script>

<template>
  <div class="header">
    <h1>
    <!--agregamos un icono al codigo a un costado del header-->
    <i 
    class="material-icons shopping-cart-icon">
    local_mall
  </i>
    {{ header }}
    </h1> 
    <!--Boton para cancelar el formulario-->
    <button v-if="editing" class="btn " v-on:click="activateEdition(false)">
      Cancelar
    </button>
    <!--Boton para agregar el formulario-->
    <button v-else class="btn btn-primary" v-on:click="activateEdition(true)">
      Agregar articulo
    </button>
  </div>
  <!--agregar el link-->
  <!--<a v-bind:href="'https://' + newItem" target="_blank">{{newItem==""?"🦖 Link":newItem}}</a>-->
  <!--<a v-bind:href="newItem === '' ? 'https://www.google.com' : 'http://' + newItem" target="_blank">
    {{ newItem === '' ? '🦖 link' : newItem }}
  </a>-->
  <a :href=link()>{{ newItem === '' ? '🦖 LINK' : newItem }}</a>
  <div>
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
  </div>

<!-- Agrupando en un div las entradas -->
 <!--<form calss="add-item form" v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item fomr">-->
<form 
class="add-item form" 
v-if="editing"
v-on:submit.prevent = "saveItem">
  
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      ALTA PRIORIDAD
    </label>
    <!-- Boton -->
    <button :disabled="newItem.length === 0"
      class="btn btn-primary"
    >
      GUARDAR PRODUCTO
    </button>
  </form>
<!--ul>li*3 es el lenguaje emet a usar-->
<!--lista para objetos-->
<ul>
        <li 
        v-for="{id,label,purchased, priority} 
        in items" 
        :key="id"
         class="amazing"
      :class="{strikeout: purchased, priority:priority}">
    {{ priority ? '❤️‍🔥' : '⭐' }} 
        {{label}} </li>

        <p v-if="items.length===0">🥀NO HAY ELEMENTOS EN LA LISTA🥀</p>
</ul>
<!--lista para arreglos-->
<ul>
  <!--<li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🦖':'🛒'}} {{label}} </li>-->
        <li 
        v-for="{id,label,purchased, priority} 
        in items" 
        :key="id"
         
      :class="[purchased ? 'strikeout' : '', priority ? 'priority' : '']">
    {{ priority ? '❤️‍🔥' : '⭐' }} 
        {{label}} 
      </li>

        <p v-if="items.length===0">🥀NO HAY ELEMENTOS EN LA LISTA🥀</p>
</ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}

</style>
