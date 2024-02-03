
<template>
  
    <h1 class="font-bold">History</h1>

   <ul>
  <li class="bg-white border-r-2 mb-1" :class="transaction.amount < 0 ? 'minus' : 'plus'" v-for="transaction in transactions" :key="transaction.id">
    <button class="text-red-700 hidden group-hover:block">X</button>
    <div class="flex justify-between">
      <span>{{ transaction.text }}</span>
      <span class="ml-4 font-bold">{{ transaction.amount }}</span>
    </div>
  </li>
</ul>
    
 
       
    
 
  
</template>

<script setup>



   const props=defineProps({
    transactions:{
        type:Array,
        required:true,
    }}
   )
  
</script>

<style>
.minus{
    border-style: solid;
  border-color: red;

}
.plus{
    border-style: solid;
  border-color: rgb(55, 199, 55);

}
button:hover {
  color: purple;
}
</style>