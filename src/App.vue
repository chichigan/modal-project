<!-- App.vue is the root components, it initially mounted to the DOM -->
<!-- All other components we make will nested in this root components -->
<template>
  <h1>{{ title }}</h1>
  <!--3) Use the components <Modal/> -->
  <Modal :header="header" :text="text" theme="sale"/>
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
      text: 'Grab your ninja swag for half price!'
    }
  },
  methods: {
    handleClick(){
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
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
