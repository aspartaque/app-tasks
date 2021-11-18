<template>
  <div id="app">

    <div class="tabs">
      <div class="tab">
        <ul class="tab__title">
          <li @click="activate(1)" :class="{ 'active' : isActive === 1 }">developer</li>
          <li @click="activate(2)" :class="{ 'active' : isActive === 2 }">designer</li>
          <li @click="activate(3)" :class="{ 'active' : isActive === 3 }">tab 3</li>
        </ul>
        <ul class="tab__content">
          <li v-show="isActive === 1">
            <CodeMirror/>
          </li>
          <li v-show="isActive === 2">
            <Colors/>
          </li>
          <li v-show="isActive === 3">Tab text 3</li>
        </ul>
      </div>
    </div>

    

  </div>
</template>

<script>
import CodeMirror from './components/CodeMirror.vue'
import Colors from './components/Colors.vue'

export default {
  name: 'App',
  components: {
    CodeMirror,
    Colors
  },
  data() {
    return {
      isActive: 1
    }
  },
  methods: {
    activate(num){
      this.isActive = num;
    }, 
  }
}

</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: #141b22;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
ul, li {
  list-style: none;
  padding: 0;
}
.tabs {
  padding-top: 40px;
}
.tab {
  width: 50%;
  margin: 0 auto;
}
.tab__title {
  display: flex;
  justify-content: space-evenly;
}
.tab__title li {
  width: 100%;
  border: 1px solid#282a36;
  padding: 10px;
  color: #8690cb;
  transition: border 200ms ease, border 200ms ease;
}
.tab__title li:hover {
  cursor: pointer;
  border: 1px solid #d34666;
  transition: border 200ms ease, border 200ms ease;
}
.tab__title li.active {
  border: 1px solid #d34666;
}
.cm-s-dracula.CodeMirror, .cm-s-dracula {
  border: 1px solid #282a36;
}
.CodeMirror-focused {
  border: 1px solid #d34666!important;
}

</style>
