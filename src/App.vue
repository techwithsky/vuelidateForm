<template>
  <div id="app">
    <h1>Vuelidate Form</h1>
    <vuelidate-form />
  </div>
  
</template>

<script>
import vuelidateForm from './components/vuelidateForm.vue';
export default {
  name: 'App',
  components: {
    vuelidateForm
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
</style>
