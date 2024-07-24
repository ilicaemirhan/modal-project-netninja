<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
      <ModalComponent ref="modalcomponent" theme="sale" @close="toggleModal()">
        <template v-slot:links>
          <a href="#">Sign Up NOW!</a>
          <a href="#">For More Info</a>
        </template>
        <h1>FREE CAT PICS! 🐈</h1>
        <p>Sign up now and get free cat pics delivered to your inbox every day!</p>
      </ModalComponent>
  </teleport>

  <teleport to=".modals" v-if="showModalDog">
    <ModalComponent @close="toggleDogModal">
        <template v-slot:links>
          <!-- <a href="#">Why are we still here?</a>
          <a href="#">Just to suffer?</a> -->
        </template>
        <h1>FREE DOG PICS! 🐶</h1>
        <p>Sign up now and get free dog pics delivered to your inbox every day!</p>
      </ModalComponent>
  </teleport>
  <button @click="toggleModal">Show Cat Modal</button>
  <button @click="toggleDogModal">Show Dog Modal</button>
</template>

<script>
import ModalComponent from './components/ModalComponent.vue'

export default {
  name: 'App',
  components: {
    ModalComponent
  },
  data(){
    return{
      title: "Hello Vue",
      header: "Sign Up for Free Cat Pics 🐈",
      text: "Don't you miss out 😎",
      showModal: false,
      showModalDog: false
    }
  },
  methods: {
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleDogModal(){
      this.showModalDog = !this.showModalDog
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
