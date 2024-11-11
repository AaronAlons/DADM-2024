<script setup>
//import ref fuction 
import {ref} from 'vue';
//usando un macro para definir las propiedades
//defineProps(['name','planIcon']);
/*defineProps({
  name: {
    type: String,
    require:true
    },
    planIcon: String,
    price:{
      type: Number,
      default: 200
      }
      });*/
const props = defineProps({
  name: {
    type: String,
    require:true
 }
});
//define event
 const emit = defineEmits(['select']);


//VARIABLE QUE PERMITE RECORDAR SI EL Plan HA SIDO SELECCIONADO
 const selected = ref(false);
 
 //FUNCION QUE PERMITE CAMBIAR EL ESTADO DE LA VARIABLE SELECTED
 const selectPlan = () => {
  selected.value =true;
  //wmitir el elvenoto de que el evento ha sido seleccionado 
 };
 emit('select', props.name);

</script>

<template>
    <div @click="selectPlan" class="plan">
    <div class="description">
      <!--vamos a habilitar las propiedades -->
      <span class="title">
        {{ name }} {{ selected ? '🦖' : '' }}
      </span>
    </div>
  </div>

</template>

<style scoped>

</style>
