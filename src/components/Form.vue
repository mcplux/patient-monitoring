<script setup>
  import { reactive } from 'vue'
  import Alert from './Alert.vue'

  const alert = reactive({
    type: '',
    message: '',
  })

  const emit = defineEmits(['update:name', 'update:owner', 'update:email', 'update:arrival', 'update:symptoms', 'save-patient'])

  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
    owner: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    arrival: {
      type: String,
      required: true,
    },
    symptoms: {
      type: String,
      required:true,
    },
  })

  const validate = () => {
    if(Object.values(props).includes('')) {
      alert.message = 'All fields are required'
      alert.type = 'error'
      return
    }

    emit('save-patient')
    alert.message = 'Patient was added successfully'
    alert.type = 'success'

    setTimeout(() => {
      alert.message = ''
      alert.type = ''
    }, 2000)
  }

</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Patient monitoring</h2>
    <p class="text-lg text-center mt-5 mb-10">
      Add patients and
      <span class="text-indigo-600 font-bold"> manege them</span>
    </p>

    <Alert 
      v-if="alert.message"
      :alert="alert"
    />

    <form @submit.prevent="validate" class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">
      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="name">Pet's name</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="text" 
          name="name" 
          id="name"
          :value="name"
          @input="$emit('update:name', $event.target.value)"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="arrival">Owner name</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="text" 
          name="owner" 
          id="owner"
          :value="owner"
          @input="$emit('update:owner', $event.target.value)"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="email">Email</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="email" 
          name="email" 
          id="email"
          :value="email"
          @input="$emit('update:email', $event.target.value)"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="arrival">Arrival date</label>
        <input 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md" 
          type="date" 
          name="arrival" 
          id="arrival"
          :value="arrival"
          @input="$emit('update:arrival', $event.target.value)"
        />
      </div>

      <div class="mb-5">
        <label class="block text-gray-700 uppercase font-bold" for="symptoms">Symptoms</label>
        <textarea
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-30"
          name="symptoms" 
          id="symptoms"
          :value="symptoms"
          @input="$emit('update:symptoms', $event.target.value)"
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
