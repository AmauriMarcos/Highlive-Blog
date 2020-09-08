<template>
    <div>
        <div class="programacao">
            <img src="" alt="">
        </div>
        <div class="pages-cards">
            <div v-for="(programacaoPost, i) in programacaoPosts" :key="i">
                 <Cards :slug='programacaoPost.slug' :title='programacaoPost.title' :image='programacaoPost.image[0].name' :category='category' :id='programacaoPost.id'></Cards>
            </div>
        </div>       
    </div>
</template>
<script>
import Cards from "../../components/Cards";
import axios from "axios";
export default {
    components:{
        Cards
    },
    data(){
        return{
            programacaoPosts: [],
            category: 'Programação'
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/categories?name=Programação")
        const posts = res.data;
        posts.map((post) =>{
            this.programacaoPosts = post.posts;
        })
    },
    
}
</script>
<style lang="scss">
    .pages-cards{
        display: grid;
        padding: 2% 9.5%;
        gap: 1rem;
        grid-template-columns: repeat(auto-fit, minmax(345px, 1fr));
    }

    .programacao{
        margin: 1rem 0 2rem 0;
        height: 18rem;
        width: 100%;
        background:linear-gradient(to right, rgba(0,0,0,.4), rgba(0,0,0,.4)), url("https://images.unsplash.com/photo-1517336714731-489689fd1ca8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=926&q=80");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;

        @include respond(phone){
            height: 10rem;
        }
    }
</style>