<script setup>

</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Patient monitoring</h2>
    <p class="text-lg text-center mt-5 mb-10">
      Add patients and
      <span class="text-indigo-600 font-bold"> manege them</span>
    </p>

    <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="pet">Pet's name</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="text" 
          name="pet" 
          id="pet"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="arrival">Owner name</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="text" 
          name="owner" 
          id="owner"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="email">Email</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="email" 
          name="email" 
          id="email"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="arrival">Arrival date</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="date" 
          name="arrival" 
          id="arrival"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="symptoms">Symptoms</label>
        <textarea
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-30"
          name="symptoms" 
          id="symptoms"
        />
      </div>

      <button 
        type="submit" 
        class="bg-indigo-600 w-full p-3 text-white font-bold uppercase hover:bg-indigo-700 cursor-pointer transition-colors"
        >
        Add patient
      </button>
    </form>

  </div>
</template>
