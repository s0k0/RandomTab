<template>
  <div>
    <div class="tabs">
        <ul>
          <li v-for="tab in tabs" v-bind:key="tab" :class="{ 'is-active': true}">
              <a @click="selectTab(tab)">{{ tab }}</a>
          </li>
        </ul>
      </div>

      <div class="tabs-details">
        
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloTab',
  data() {
        return { 
          tabs: ['one','two','three'] 
          };
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
  cursor: pointer;
}
</style>
