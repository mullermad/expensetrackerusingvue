
<template>
  <div class="flex h-screen items-center justify-center bg-gray-200">
  
 
  <div>
    <Header /> 
  <div>
<Balance :total="total"/>
<IncomeExpense :income="income" :expense="expense"/>
<TransactionList :transactions="transactions" />
<AddTransaction />
  </div>
  
  </div>
  </div>
</template>


<script setup>
import {ref,computed} from 'vue'
import Header from './components/Header.vue'
import Balance from './components/Balance.vue'
import IncomeExpense from './components/IncomeExpense.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'


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

          },0).toFixed(2)
          
        });

         //get expense
        const expense=computed(()=>{
          return transactions.value.filter((transaction)=>transaction.amount<0)
          .reduce((accumulator,transaction)=>{
            return accumulator+transaction.amount;

          },0).toFixed(2)
          
        });

        

</script>