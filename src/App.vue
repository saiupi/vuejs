<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div class="cards">
      <Article v-for="article in articles" 
      :key="article.id" :articles="article" @change-name="updateName">
      </Article>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Article from '@/components/Article.vue'
import eventbus from '@/eventbus'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Article
  },
  data() {
    return {
      msg: 'Hello world',
      show: true,
      articles: [
        {
          id: 1,
          title: 'title 1',
          description: 'description 1',
        },
        {
          id: 2,
          title: 'title 2',
          description: 'description 2',
        },
        {
          id: 3,
          title: 'title 3',
          description: 'description 3',
        },
      ],
    }
  },
   created() {
    eventbus.$on('pass-message', (data) => {
      this.updateName(data,"ppppppppp")
    })
  },
  methods:{
    updateName(data){
      console.log(data,"ddddd")
      this.articles.forEach((item)=>{
        if(item.id===data.id){
          item.title=data.title
        }
      })
    }
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
