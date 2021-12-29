<template>
  <main>
    <div class="upper">
      <button v-on:click="handleClick('AC')">AC</button>
      <div class="screen">
        <span>{{ screen }}</span>
      </div>
    </div>
    <div class="keyboard">
      <button 
        v-for="(key, index) in mainKeys" 
        v-bind:key="index"
        v-on:click="handleClick(key)"
      >{{ key }}</button>
    </div>
  </main>
</template>

<script>
  export default {
    name: 'Calculator',
    data: () => ({
      screen: '0',
      lastPressedKey: null,
      mainKeys: [
        '7', '8', '9', '/',
        '4', '5', '6', '*',
        '1', '2', '3', '-',
        '0', '.', '=', '+',
      ]
    }),
    methods:{
      handleClick(key) {

        if(key === 'AC') {
          this.handleClear();

        } else if(key === '=') {
          this.handleEqual();

        } else if(key === '.' && this.screen.indexOf('.') !== -1) {
          return;

        } else if(this.lastPressedKey === '=' || (this.screen === '0' && key !== '.')) {
          this.screen = key;

        } else {
          this.screen += key;

        }
    
        this.lastPressedKey = key;
      },

      handleClear() {
        this.screen = '0';
      },

      handleEqual() {
        this.screen = eval(this.screen);
      },
      
    }
  }
</script>

<style scoped>

  main {
    min-width: 300px;
    width: 400px;

    background-color: #aaaaba;
    border-radius: 10px;

  }

  .upper {
    display: flex;
    align-items: stretch;
  }

  .upper > button {
    border-radius: 10px 0 0 0;
  }

  .screen {
    background-color: #0a0a0a;
    color: white;
    flex: 1;

    text-align: right;
    padding: 25px 10px;
    font-size: 4rem;
    border-radius: 0 10px 0 0;

    overflow: hidden;
    text-overflow: ellipsis;

  }

  .keyboard {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }

  button {
    background-color: #4b4b4b;
    color: white;
    font-size: 3rem;
    padding: 10px;
  }

  button:nth-child(4n) {
    background-color: #0082ce;
  }
  
</style>
