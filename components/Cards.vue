<template>
    <nuxt-link :to="`/${slug}`" class="wrap-link">
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
    props: ['title', 'category','image', 'id', 'slug'],
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
            
            @include respond(phone){
                height: 250px !important;
                position: relative;
                
            }
        }

        &__category{
            padding: 1rem 2rem;
            background-color: #fff;
            transform: translateY(-3rem);
            text-transform: uppercase;
            font-family: 'Open Sans', sans-serif;
            font-weight: 300;

            @include respond(phone){
                margin: 0 !important;
                font-size: .9rem;
                padding: .7rem 1.4rem;
                transform: translateY(-2rem) !important;
               
            }
        }

        &__title-card{
            @include sub-titulo;
            transform: translateY(-3rem);

            @include respond(phone){
                font-size: 1.3rem !important;
                transform: translateY(-2rem);
                margin-bottom: 0 !important;
                margin-top: 2rem;
            }
        }
    }
</style>