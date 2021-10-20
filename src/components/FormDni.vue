<template>
  <div>
    <div class="d-contents">
      <!-- This is an example component -->
      <div v-if="stepper === 1" class="mx-auto" style="width: 35%">
        <img class="w-64 bg-cover mx-auto" src="./../assets/logo.jpeg" alt="">
        <form class="w-full">
          <div class="mb-6">
            <label for="dni" class="text-sm font-medium text-gray-900 block mb-2">Cédula</label>
            <input type="text" id="dni" v-model="dni" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" placeholder="26374098" required="">
          </div>
          <button
              type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
              @click="stepper = 2"
          >
            Siguiente
          </button>
        </form>
      </div>

      <camera v-if="stepper === 2" @take-picture="takePicture" class="max-w-lg mx-auto" />
      <div v-if="stepper ===3" class="w-full">
        <div v-if="isLoading" class="text-center">
          Cargando
        </div>

        <div v-if="messageError" class="text-center">{{messageError}}</div>

        <show-info v-if="Object.keys(person).length" />
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios'
import Camera from "./Camera";
import ShowInfo from "./ShowInfo";

export default {
  components: {ShowInfo, Camera},
  data:() => ({
    dni: '',
    picture: '',
    stepper: 1,
    messageError: null,
    isLoading : false,
    person: {}
  }),
  methods: {
    async getDataUser(){
      this.isLoading = true
      const data = {
        dni: this.dni,
        picture: this.picture
      }
      try {
        const response = await axios.post('https://api.zeye.io/persons/dni-auth', data)
        this.person = response.data.data
        // console.log(response)
      } catch (error) {
        console.info(error.response.data.message)
        this.messageError = error.response.data.message
      }

      this.isLoading = false
    },
    takePicture(picture) {
      this.picture =  picture
      this.getDataUser()
      this.stepper = 3


      console.info('picture', picture)
    }
  }
}
</script>
