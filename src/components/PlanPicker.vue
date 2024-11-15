<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import { ref } from 'vue';
// creando una referencia reactiva para el plan seleccion
const selectedPlan = ref(null);
const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPlan = (name) => {
  //almacenar el plan seleccion
  selectedPlan.value = name;
};
</script>

<template>
  <div class="plans">
    <PlanPickerItem
     v-for="plan in plans" 
     :key="plan" 
     :name="plan"
     @select="selectPlan"
     :selectPlan="selectPlan"></PlanPickerItem>
  </div>
  <p> {{ selectedPlan }}</p>
</template>

<style scoped></style>