<template>
    <div class="plan">
    <div class="description">
      <!--vamos a habilitar las propiedades -->
      <span class="title">
        {{ name }}
      </span>
    </div>
  </div>

</template>

<script setup>
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
defineProps({
 name: {
  type: String,
  require:true
 }
});
</script>

<style scoped>

</style>
