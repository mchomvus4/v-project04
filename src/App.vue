<template>
  <Form/>
  <Footer/>
</template>

<script>

import Form from './components/Form'
import Footer from './components/Footer'
export default {
  name: 'App',
  components: {
  Form,
  Footer
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
body{
  margin: 0;
  background: #487eb0;
}
</style>
