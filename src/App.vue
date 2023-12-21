<script setup>
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'
  import Patient from './components/Patient.vue'
  import { reactive, ref } from 'vue';

  const patients = ref([])

  const pet = reactive({
    name: '',
    owner: '',
    email: '',
    arrival: '',
    symptoms: '',
  })

  const savePatient = () => {
    patients.value.push({...pet})

    pet.name = ''
    pet.owner = ''
    pet.email = ''
    pet.arrival = ''
    pet.symptoms = ''
  }
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />

    <div class="mt-12 md:flex">
      <Form 
        v-model:name="pet.name"
        v-model:owner="pet.owner"
        v-model:email="pet.email"
        v-model:arrival="pet.arrival"
        v-model:symptoms="pet.symptoms"
        @save-patient="savePatient"
      />

      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Patient list</h3>

        <div v-if="patients.length > 0">
          <p class="text-lg text-center mt-5 mb-10">
            <span class="text-indigo-600 font-bold">Patient </span>
            Information
          </p>  
          <Patient v-for="patient in patients" :patient="patient" />
        </div>
        <p v-else class="mt-20 text-2xl text-center">There are no patients yet</p>
      </div>
    </div>
  </div>
</template>
