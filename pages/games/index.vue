<template>
    <div>
        <div class="game">
            <img src="" alt="">
        </div>
        <div class="pages-cards">
            <div v-for="(game, i) in games" :key="i">
                 <Cards :slug='game.slug' :id='game.id' :title='game.title' :image='game.image[0].name' :category='category'></Cards>
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
            games: [],
            category: 'Games'
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/categories?name=Games")
        const posts = res.data;
        posts.map((post) =>{
            this.games = post.posts;
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

        @include respond(phone){
            padding: 2% 5%;
            gap: .6rem;
        }
    }

    .game{
        margin: 1rem 0 2rem 0;
        height: 18rem;
        width: 100%;
        background:linear-gradient(to right, rgba(0,0,0,.4), rgba(0,0,0,.4)), url("https://images.unsplash.com/photo-1580234797602-22c37b2a6230?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1047&q=802");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;

        @include respond(phone){
            height: 10rem;
        }
    }
</style>