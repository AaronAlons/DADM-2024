        <script setup>
        
        import PlanPickerItem from './PlanPickerItem.vue';
        import {ref} from 'vue';
        const plans = ref(['El soltero', 'El curioso','El adicto']);
        const selectPlan = (name)=>{console.log(name)};
        </script>
<template>
    
    <!--<plan-item :price="100" plan-icon="🍵" name="El soltero"></plan-item>
    <plan-item :price="200" plan-icon="🍵" name="El curioso"></plan-item>
    <plan-item :price="300" plan-icon="🍵" name="El adicto"></plan-item>-->
    <div class="plans">

      <PlanPickerItem 
      v-for="plan in plans" 
      :key="plan" 
      :name="plan"
     @select ="(name) => selectPlan(name)"
     />

   </div>
</template>

<style scoped>

</style>