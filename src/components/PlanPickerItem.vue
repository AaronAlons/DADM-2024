<template>
  <div  @click="selectPlan" class="plan">
    <div class="description">
      <span class="title"> {{ name }} {{ IsSelected ? '🦖' : '' }}</span>
    </div>
  </div>
</template>

<script setup>
//importamos la funcion para crear una propiedad computada
import { computed } from 'vue';
// Usando un macro para
// definir las props
//defineProps(['name','planIcon']);
//esto es un esquema
const props = defineProps({
  name: {
    tyoe: String,
    required: true
  },
  //definicion sencilla 
  selectPlan: String
});
// Definiendo un evento
const emit = defineEmits (['select']);

// Función que permite cambiar el estado de la variable 
// selected 
const selectPlan = () => {
  // Emitir evento de que el 
  //plan ha sido seleccionado
  emit('select', props.name);
}
//creamos una property computed para saber si el plan ha sido seleccionado
 const isSelected = computed(() => {
  return props.selectPlan === props.name;
});

</script>

<style scoped>

</style>