<template>
  <div class="article">
    <h3>{{articles.title}}</h3>
    <p>{{articles.description}}</p>
    <button @click="changeName">Change Title</button>
    <SubArticle :id="articles.id"></SubArticle>
  </div>
    
</template>
<script>
import SubArticle from '@/components/SubArticle.vue'

export default {
  components:{
    SubArticle,
  },
props: {
    articles: {
      required: true,
      type: Object,
    },
  },
  data() {
    return {
      title: 'article title',
      description: 'description',
    }
  },
methods: {
    changeName() {
      this.$emit('change-name', {
        title: 'New article title',
        id: this.articles.id,
      })
    },
  },
}


</script>
<style scoped>
.article {
  width: 150px;
  height: 200px;
  border: 1px solid black;
  border-radius: 5px;
  padding: 10px;
}
</style>
