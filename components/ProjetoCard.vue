<template>
    <nuxt-link :to="`/${slug}`" class="wrap-link">
        <div class="cards">
            <div class="cards__contador">
                <h2>{{contador}}</h2>
            </div>
            <img class="cards__img" :src="`${image}`" alt="">
            <p class="cards__category">{{category}}</p>
            <h2 class="cards__title-card">{{title}}</h2>
        </div>
    </nuxt-link>
</template>

<script>
import axios from "axios";
export default {
    props: ['title', 'category','image', 'id', 'contador', 'slug'],
}
</script>

<style lang="scss">
@font-face {
        font-family: 'Higher Jump';
        src: url('~assets/fonts/Higher Jump.ttf') format('truetype');
        font-style: normal;
        font-weight: normal;      
    }  
    .cards{
        @include center;
        flex-direction: column;
        position: relative;
        z-index: 2;

        &__img{
            height: 345px;
            width: 100%;
            object-fit: cover;   
        }

        &__category{
            padding: 1rem 2rem;
            background-color: #fff;
            transform: translateY(-3rem);
            text-transform: uppercase;
            font-family: 'Open Sans', sans-serif;
            font-weight: 300;
            z-index: 3;

            
        }

        &__title-card{
            @include sub-titulo;
            transform: translateY(-3rem);
        }

        &__contador{           
            height: 5rem;
            width: 5rem;
            position: absolute;
            top: 0;
            right: 0;
            z-index: 20;
            background-color: rgba(197, 30, 37,.7);
            color: black;   
            @include center;

            @include respond(phone){
                height: 4rem;
                width: 4rem;
            }

            & h2{
                font-size: 1.3rem;
                color: rgb(255, 255, 255);
                font-family: 'Higher Jump';

                @include respond(phone){
                    font-size: 1rem;
                }
            }
        }
    }
</style>