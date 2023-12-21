<script setup>
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'
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
    patients.value.push(pet)
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
    </div>
  </div>
</template>
