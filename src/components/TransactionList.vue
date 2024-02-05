
<template>
  
    <h1 class="font-bold">History</h1>

   <ul>
  <li class="bg-white border-r-2 mb-1" :class="transaction.amount < 0 ? 'minus' : 'plus'" v-for="transaction in transactions" :key="transaction.id">
  
    <div class="flex justify-between">
      <button @click="handleClick(transaction.id)" class="text-red-700 inline">X</button>
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
  
const emit=defineEmits(['transactionDeleted']);

  const handleClick=(id)=>{
  
    emit('transactionDeleted',id)
     console.log('sucessfully deleted');
  }

 
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