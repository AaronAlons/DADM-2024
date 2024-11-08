        <script setup>
        
        import PlanItem from './PlanItem.vue';
        import {ref} from 'vue';
        const plans = ref(['El soltero', 'El curioso','El adicto']);
        </script>
<template>
    
    <!--<plan-item :price="100" plan-icon="🍵" name="El soltero"></plan-item>
    <plan-item :price="200" plan-icon="🍵" name="El curioso"></plan-item>
    <plan-item :price="300" plan-icon="🍵" name="El adicto"></plan-item>-->
    <div class="plans">

      <PlanItem v-for="plan in plans" :key="plan" :name="plan"></PlanItem>
    </div>
</template>

<style scoped>

</style>