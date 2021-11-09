<template>
  <div id="colors">
    <h2>Which color with this hex-code?</h2>
    <h3>{{ randColor }}</h3>
    <button @click="random" class="btn">RANDOM</button>
    <div class="grid">
      <div class="el color-1"></div> 
      <div class="el color-2"></div> 
      <div class="el color-3"></div> 
      <div class="el color-4"></div> 
    </div>
  </div>
</template>

<script>
// import Vue from 'vue'

// var colorsAll = {
//   red: '#f00',
//   green: '#00ff00',
//   blue: '0000ff',
//   black: '#333'
// }

export default {
  el: '#colors',
  data () {
    return {
      colors: [
        '#f00',
        '#00ff00',
        '#0000ff',
        '#333'
      ],
      randColor: '#333',
    }
  },
  methods: {
    random() {
      const idx = Math.floor(Math.random() * this.colors.length);
      this.randColor = this.colors[idx]
    }
  }
};
</script>

<style>
  #colors {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .grid {
    display: grid;
    grid-template-columns: 40px 40px;
    grid-gap: 10px;
    margin-top: 40px;
  }
  .el {
    width: 40px;
    height: 40px;
  }
  .color-1 {
    background: #333;
  }
  .color-2 {
    background: #f00;
  }
  .color-3 {
    background: #00ff00;
  }
  .color-4 {
    background: #0000ff;
  }
</style>