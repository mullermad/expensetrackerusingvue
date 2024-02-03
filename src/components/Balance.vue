
<template>
  
    <h1 class="mt-3">Your balance is :</h1>
  <h3 class="font-bold mb-3 text-lg">${{total}}</h3>

 
  
</template>

<script setup>
const props=defineProps({
  total:{
    type:Number,
    required:true

  }
});
</script>