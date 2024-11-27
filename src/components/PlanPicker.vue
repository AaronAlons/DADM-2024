<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref, onMounted } from 'vue';

// creando una referencia reactiva para el plan seleccionado
const selectedPlan = ref(null);

// lista de planes
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);

// función que permite almacenar el plan seleccionado
const selectPlan = (name) => {
  // almacenar el plan seleccionado
  selectedPlan.value = name;
};

// referencia al elemento del componente que contiene los planes
const plansWrapper = ref(null);


//intentar obtener la referencia del plans
console.log('Termina de ejecutar el script setup🦖');

// Se ejecuta cuando el componente está montado

onMounted(() => {
  // intentar obtener la referencia del plans
  console.log('El componente planpicker está montado');
  console.log(plansWrapper.value);

});
</script>

<template>
  <div ref='plansWrapper' class="plans">
    <PlanPickerItem
      v-for="plan in plans" 
      :key="plan" 
      :name="plan"
      :selectPlan="selectedPlan"
      @select="selectPlan" 
    />
  </div>
</template>

<style scoped>
/* Estilos del componente padre (si son necesarios) */
</style>
