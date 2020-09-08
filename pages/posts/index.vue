<template>
    <div>
        <div class="pages-cards">
            <div v-for="(post, i) in posts" :key="i">
                 <Cards :slug='post.slug' :id='post.id' :title='post.title' :image='post.image[0].name' :category='post.categories[0].name'></Cards>
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
            posts: [],
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        this.posts = res.data;
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

   
</style>