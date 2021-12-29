<template>
  <Calculator />
</template>

<script>
  import Calculator from './components/calculator';
  export default {
    name: 'App',
    components: {
      Calculator
    },
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  html, body, #app {
    height: 100%;
    margin: 0;
  }

  #app {
    background-color: #eaeaea;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  * {
    font-family: 'Roboto', sans-serif;
  }
  
</style>

