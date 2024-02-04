
<template>
  <div class="flex h-screen items-center justify-center bg-gray-200">
  
 
  <div>
    <Header /> 
  <div>
<Balance :total="+total"/>
<IncomeExpense :income="+income" :expense="+expense"/>
<TransactionList :transactions="transactions" />
<AddTransaction @transactionSubmitted="handleTransactionSubmitted"/>
  </div>
  
  </div>
  </div>
</template>


<script setup>
import {ref,computed} from 'vue'
import {useToast} from 'vue-toastification'
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'
 
const toast=useToast();

 const  transactions=ref([
            {id:1,text:"flower",amount:-19.9},
            {id:2,text:"salary",amount:219.9},
            {id:3,text:"book",amount:-19.9},
            {id:4,text:"camera",amount:90.9},
        ]);
//get total
        const total=computed(()=>{
          return transactions.value.reduce((accumulator,transaction)=>{
            return accumulator+transaction.amount;

          },0)
          
        });
        //get income
        const income=computed(()=>{
          return transactions.value.filter((transaction)=>transaction.amount>0)
          .reduce((accumulator,transaction)=>{
            return accumulator+transaction.amount;

          },0)
          
        });

         //get expense
        const expense=computed(()=>{
          return transactions.value.filter((transaction)=>transaction.amount<0)
          .reduce((accumulator,transaction)=>{
            return accumulator+transaction.amount;

          },0)
          
        });

        //to generate unique id 
function generateUniqueId() {
  const timestamp = new Date().getTime(); // Get current timestamp
  const randomNum = Math.random(); // Generate a random number
  const uniqueId = `${timestamp}-${randomNum}`; // Combine timestamp and random number
  
  return uniqueId;
};

//add transaction
        const handleTransactionSubmitted=(transactionData)=>{
          transactions.value.push({
            id:generateUniqueId(),
            text:transactionData.text,
            amount:transactionData.amount
          })
          toast.success('Transaction sucessfully added')
        }

        

</script>