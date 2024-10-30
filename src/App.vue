<script setup>
import { ref, computed } from 'vue';
// Modo edición
const editing = ref(false);
// Funcion que alterna el valor de la variable editing
const doEdit = (edit) => {
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};

const header = ref('App Lista de compras');
const items = ref([
  { id: 1, label: 'Cafe', purchased: true, highPriority: true },
  { id: 2, label: 'Un pan de muerto', purchased: false, highPriority: true },
  { id: 3, label: '3 seviches', purchased: true, highPriority: false },
  { id: 4,label:'10 bolillos',purchased:true,priority:true},
  { id: 5 ,label:'1 lata de frijoles',purchased:false, priority:true},
  { id: 6,label:'1 chela',purchased:false, priority:true},
  { id: 7,label:'1 nutella',purchased:false, priority:true},
  { id: 8,label:'1 lata de atun', purchased:false,  priority:true},
  { id: 9,label:'1 pc gamer', purchased:false,  priority:true}
]);
const newItem = ref('');
const newItemHighPriority = ref(false);
// Metodo para agregar nuevos elementos a la lista
const saveItem = () => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    highPriority: newItemHighPriority.value
  });
  // Reiniciendo la entrada de texto
  newItem.value = "";
  newItemHighPriority.value = false;
};
// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

// Propiedad computada
const characterCount = computed(() => {
  return newItem.value.length;
});
// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => [...items.value].reverse());
</script>

<template>
  <div class="header">
    <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
    <button v-if="editing" @click="doEdit(false)" class="btn">Cancelar</button>
    <button v-else @click="doEdit(true)" class="btn btn-primary">Agregar Articulo</button>
  </div>
  <!-- Agrupando Entradas de usuario -->
  <form class="add-item form" v-if="editing" v-on:submit.prevent="saveItem">
    <!-- Entrada de texto -->
    <input type="text" placeholder="Add Item" v-model.trim="newItem">
    <!-- Radio Buttons -->
    <label><input type="checkbox" v-model="newItemHighPriority">Alta Prioridad</label>
    <!-- Boton -->
    <button :disabled="newItem.length === 0" class="btn btn-primary">
      Guardar compra
    </button>
  <!-- Contador -->
  <p class="counter">
    {{characterCount}} / 200
  </p>
  </form>
  <!-- Lista -->
  <ul>
    <li v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
      :class="{ strikeout: purchased, priority: highPriority }" @click="togglePurchased(reversedItems[index])" v-bind:key="id">
      🦖 {{ label }}
    </li>
  </ul>
  <p v-if="items.length === 0">🥀 No hay elementos en la lista</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
  /* Adjust the font-size value as per your desired size */
}
</style>