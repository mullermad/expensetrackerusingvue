<template>
  <div class="flex bg-white p-2 ml-0 m-2  justify-between">
   <div class="mr-10">
    <h2>Income is :</h2>
    <h3 class="text-green-400 font-bold">+${{income}}</h3>
   </div>
 
 
   <div>
    <h2>Expense is :</h2>
    <h3 class="text-red-700 font-bold">-${{expense}}</h3>
   </div>
   </div>
</template>

<script setup>

const props=defineProps({
  income:{
    type:Number,
    required:true
  },
  expense:{
    type:Number,
    required:true
  }
})
</script>