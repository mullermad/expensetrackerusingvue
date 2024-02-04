<template>
  <div class="flex justify-center items-center mt-2">
    <form @submit.prevent="onSubmit" class="bg-gray-100 p-8 rounded shadow-lg">
      <div class="mb-4">
        <label for="name" class="text-lg font-semibold">Text:</label>
        <input type="text" id="text" v-model="text" placeholder="enter text" class="border border-gray-300 rounded px-3 py-2 mt-1 w-full" />
      </div>
      <div class="mb-4">
        <label  class="text-lg font-semibold">Amount:</label>
        <input type="text" id="amount" v-model="amount" placeholder="please enter amount" class="border border-gray-300 rounded px-3 py-2 mt-1 w-full" />
      </div>
      <button type="submit" class="bg-purple-400 hover:bg-purple-600 text-white w-full font-semibold py-2 px-4 rounded">Submit</button>
    </form>
  </div>
</template>



<script setup>
import { ref } from 'vue';
import {useToast} from 'vue-toastification'

const text=ref('')
const amount=ref('')
const toast=useToast();


const emit=defineEmits(['transactionSubmitted']);


const onSubmit=()=>{
if(!text.value || !amount.value){
  toast.error('Both feilds must be filled');
  return;

}

const transactionData={
  text:text.value,
  amount:parseFloat(amount.value)
};

emit('transactionSubmitted',transactionData)


text.value='';
amount.value='';
}
</script>

