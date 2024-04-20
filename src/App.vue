<!-- App.vue is the root components, it initially mounted to the DOM -->
<!-- All other components we make will nested in this root components -->
<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>

  <!--3) Use the components <Modal/> -->
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <!-- Pass template in to <slot name="links"> -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>

      <!-- Pass value in to default <slot> -->
      <h1>Ninja Giveaway</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </div>

  <!-- @click.right is event modifier, when right click mouse will fire -->
  <button @click.right="toggleModal">Open Modal</button>
  <button @click="toggleModalTwo">Open Modal 2</button>
</template>

<script>
//How to use components
//1) Import components first
import Modal from './components/Modal.vue'

//2) Register inside components
export default {
  name: 'App',
  components:{ Modal },
  data(){
    return {
      title: 'My First Vue App :)',
      header: 'Sign up for the giveaway',
      text: 'Grab your ninja swag for half price!',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app {
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
