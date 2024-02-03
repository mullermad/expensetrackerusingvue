<template>
  <div class="flex justify-center items-center mt-2">
    <form @submit.prevent="submitForm" class="bg-gray-100 p-8 rounded shadow-lg">
      <div class="mb-4">
        <label for="name" class="text-lg font-semibold">Text:</label>
        <input type="text" id="name"  class="border border-gray-300 rounded px-3 py-2 mt-1 w-full" />
      </div>
      <div class="mb-4">
        <label  class="text-lg font-semibold">Amount:</label>
        <input  id="number" class="border border-gray-300 rounded px-3 py-2 mt-1 w-full" />
      </div>
      <button type="submit" class="bg-purple-400 hover:bg-purple-600 text-white w-full font-semibold py-2 px-4 rounded">Submit</button>
    </form>
  </div>
</template>



<script>
</script>

