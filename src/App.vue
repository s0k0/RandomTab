<template>
  <div id="app">
    <h1>Hello Random Browser Site<span>Select a tab ;)</span></h1>
    <HelloTab/>
  </div>
</template>

<script>
import HelloTab from './components/HelloTab.vue'

export default {
  name: 'app',
  components: {
    HelloTab
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: gray;
}
h1 {
  span {
    margin-left: 12px; 
    font-size: small;
  }
  @media(max-width: 600px) {
    display: flex;
    flex-direction: column;
    margin-bottom: 24px; 
    text-align: center
  }
}
</style>
