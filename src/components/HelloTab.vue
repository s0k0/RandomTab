<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/1.20.3/TweenMax.min.js"></script>
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
      <div v-if="selectedTab.name ==='Topics'" class="tabs-topics-details">
         <div v-for="item in topics" v-bind:key="item.title">
           <span class="topics-title">{{item.title}}</span>
           <span class="topics-posts">{{item.posts}} POSTS</span>
         </div>
      </div>
       <div v-if="selectedTab.name ==='Archive'" class="tabs-archive-details">
         <div v-for="(item,index) in archives" v-bind:key="index" class="">
           <img :src="require(`@/assets/grumpyCat${index}.jpeg`)"/>
           {{ item }}
          </div>
      </div>
      <div v-if="selectedTab.name ==='Pages'" class="tabs-pages-details">
        <h1 id="my-color">{{ myColor }}</h1>
        <button id="change-color" v-on:click="generateColor">New Color</button>
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
        myColor: '#000000'
        };
  },
  created(){
    const index = Math.floor(Math.random() * this.tabs.length)
    this.selectTab(this.tabs[index])
  },
  computed: {
    archives: () => {
      return Array.from(Array(10), (x,index) => 'Grumpy Cat Contribute Nr.'.concat(index))
    },
    topics: () => {
      const list = ['HTML Techniques', 'CSS Styling', 'Flash Tutorials', 'Web Miscanella', 'Site News', 'Web Development']
      return list.map( title => { return { title, posts: Math.floor(Math.random() * 100 ) } })
    },
    pages: () => {
      return Array.from(Array(10), (x,index) => 'Pages number'.concat(index))
    }
  },
  methods: {
    selectTab(selectedTab) {
        this.selectedTab = selectedTab
    },
    generateColor: function(event){
        this.myColor = '#'+(Math.random()*0xFFFFFF<<0).toString(16)
        document.body.style.background = this.myColor
      }
  }
}
</script>

<style scoped  lang="scss">
.tabs-container {
  padding: 24px;
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
  margin: 0 12px 0 0;
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
.tabs-archive-details {
  display: flex;
  flex-direction: column;
  div {
    @media(max-width: 500px) {
      flex-direction: column;
      margin-bottom: 24px; 
    }
    display: flex;
    justify-content: flex-start;
    align-items: center;
  }
  img {
    max-width: 100px;
    padding: 12px; 
  }
}
.tabs-topics-details {
  padding: 12px;
  div {
    padding: 12px;
    border-bottom: 1px solid lightgray; 
  }
  .topics-posts {
      padding-left: 12px;
      color: gray;
      font-size: x-small;
  }
}
.tabs-pages-details {
    h1 { 
      text-align: center;
      color: white;
    }
    button#change-color {
      position: relative;
      display: block;
      margin: 0 auto;
      width: 140px;
      height: 30px;
      border-radius: 30px;
      color: #000000;
      background: #fff;
      border: 1px solid grey;
      font-weight: bold;
      font-size: 12px;
      cursor: pointer;
      outline: none;
    }
  }
</style>
