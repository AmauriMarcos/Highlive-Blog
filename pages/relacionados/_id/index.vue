<template>
    <div class="tag-results">
        <h2 class="tag-title">Tag: <span class="tag-palavra-pesquisada">{{$route.params.id}}</span></h2>
        <div v-for="result in results" :key='result.id' class="category-id-page__article" >
            <HorizontalArticle
                :slug='result.slug'
                :title='result.title'
                :body='result.body'
                :image='result.image[0].name'
                :id='result.id'
                :category='result.categories[0].name'
                v-if="!empty"
            ></HorizontalArticle>
        </div>
    </div>
</template>

<script>
import HorizontalArticle from "../../../components/HorizontalArticle";
import axios from "axios";
export default {
    components:{
        HorizontalArticle
    },
    data(){
        return{
            results: [],
            empty: false
        }
    },
    async created(){
       const res = await axios.get(`https://amauri-blog.herokuapp.com/tags?name=${this.$route.params.id}`)  
       const myData = res.data;
       myData.map((post) =>{
           this.results = post.posts
       }) 
   
    },
    
   
}
</script>

<style lang="scss">
  .tag-results{
      margin-top: 3rem;
  }

  .tag-title{
      @include sub-titulo;
  }

  .tag-palavra-pesquisada{
      @include palavra-pesquisada;
  }
</style>