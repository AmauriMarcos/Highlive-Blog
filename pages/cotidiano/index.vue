<template>
    <div>
        <div class="cotidiano">
            <img src="" alt="">
        </div>
        <div class="pages-cards">
            <div v-for="(cotidianoPost, i) in cotidianoPosts" :key="i">
                 <Cards :id='cotidianoPost.id' :title='cotidianoPost.title' :image='cotidianoPost.image[0].name' :category='category'></Cards>
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
            cotidianoPosts: [],
            category: 'Cotidiano'
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/categories?name=Cotidiano")
        const posts = res.data;
        posts.map((post) =>{
            this.cotidianoPosts = post.posts;
        })
    }
}
</script>
<style lang="scss">
    .pages-cards{
        display: grid;
        padding: 2% 9.5%;
        gap: 1rem;
        grid-template-columns: repeat(auto-fit, minmax(345px, 1fr));
    }

    .cotidiano{
        margin: 1rem 0 2rem 0;
        height: 18rem;
        width: 100%;
        background: url("https://images.unsplash.com/photo-1597645945152-b3f45cfb00e7?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }
</style>