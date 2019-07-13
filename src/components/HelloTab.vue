<template>
  <div class="tabs-container">
    <div class="tabs">
        <ul>
          <li v-for="tab in tabs" v-bind:key="tab.id" :class="{ 'is-active': tab.name === selectedTab.name}">
              <a @click="selectTab(tab)">{{ tab.name }}</a>
          </li>
        </ul>
      </div>
      <hr>
      <div class="tabs-details">
         <p v-for="item in content" v-bind:key="item">{{ item }}</p>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloTab',
  data() {
      return { 
        tabs: [
          { name: 'Topics', id: '1'},
          { name: 'Archive', id: '2'},
          { name: 'Pages', id: '3'}
          ] ,
        selectedTab: {},
        content: []
        };
  },
  created(){
    const index = Math.floor(Math.random() * this.tabs.length)
    this.selectTab(this.tabs[index])
  },
  methods: {
    selectTab(selectedTab) {
        this.selectedTab = selectedTab
        this.content = this.randomTopics(selectedTab.name)
    },
     randomTopics: (tabName) => {
      const counter = Math.floor(Math.random() * 10) + 1
      return Array.from(Array(counter), (x,index) => tabName.concat(index + 1))
    }
  }
}
</script>

<style scoped  lang="scss">
.tabs-container {
  padding: 12px;
  background: rgba(66,185,131,0.1);
  text-align: left
}
ul {
  list-style-type: none;
  padding: 0;
  margin: 0
}
li {
  display: inline-block;
  margin: 12px 12px 0 0;
  font-size:larger
}
a {
  color: grey;
  cursor: pointer;
}
.is-active {
  a {
    color: #42b983;
  }
}
</style>
