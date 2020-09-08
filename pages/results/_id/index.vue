<template>
    <div>
        <h2 v-if="!empty" class="title-result">Todos os resultados para: <span class="palavra-pesquisada">{{$route.params.id}}</span></h2>
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
        <div class="no-results" v-if="empty">
            <h2 class="title-result">Nenhum resultado encontrado para: <span class="palavra-pesquisada">{{$route.params.id}}</span></h2>
            <Search></Search>
        </div>
    </div>
</template>

<script>
import HorizontalArticle from "../../../components/HorizontalArticle";
import Search from "../../../components/Search";
import axios from "axios";
export default {
    components:{
        HorizontalArticle,
        Search
    },
    data(){
        return{
            results: [],
            empty: false
        }
    },
    async created(){
       const res = await axios.get(`https://amauri-blog.herokuapp.com/posts?title_contains=${this.$route.params.id}`)
            
        if(typeof res.data !== 'undefined' && res.data.length > 0){
            this.results = res.data
            this.empty = false;
        }else{             
            this.empty = true
        }                
    },
    
   
}
</script>

<style lang="scss">
    .title-result{
        @include sub-titulo;
        margin-top: 2rem;
    }

    .palavra-pesquisada{
        @include palavra-pesquisada
    }
</style>