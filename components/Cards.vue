<template>
    <nuxt-link :to="`/${id}`" class="wrap-link">
        <div class="cards">
            <img class="cards__img" :src="`${image}`" alt="">
            <p class="cards__category">{{category}}</p>
            <h2 class="cards__title-card">{{title}}</h2>
        </div>
    </nuxt-link>
</template>

<script>
import axios from "axios";
export default {
    props: ['title', 'category','image', 'id'],
    data(){
        return{
            cards: []
        }
    },
    async fetch(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        const articles = res.data.slice(3,6)
        this.cards = articles
    }
}
</script>

<style lang="scss">
    .cards{
        @include center;
        flex-direction: column;

        &__img{
            height: 345px !important;
            width: 100% !important;
            object-fit: cover !important;
            
        }

        &__category{
            padding: 1rem 2rem;
            background-color: #fff;
            transform: translateY(-3rem);
            text-transform: uppercase;
            font-family: 'Open Sans', sans-serif;
            font-weight: 300;
        }

        &__title-card{
            @include sub-titulo;
            transform: translateY(-3rem);
        }
    }
</style>