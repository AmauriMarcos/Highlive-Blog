<template>
    <nuxt-link :to="`/${id}`" class="wrap-link">
    <div class="horizontal">
        <div class="horizontal__image-box">
            <img :src="`${image}`" alt="" >
        </div>
        <div class="horizontal__info">            
            <p class="horizontal__info-category">{{category}}</p>
            <h2 class="horizontal__info-title">{{title}}</h2>  
            <p class="horizontal__info-body" v-html="content">{{content}}<p/>  
            <button class="horizontal__info-btn">Continuar lendo</button>           
        </div>     
    </div>   
    </nuxt-link>
</template>

<script>
/* MARKDOWN CODE */
const md = require('markdown-it')({
    html: true,
    linkify: true,
    typographer: true,
})
.use(require('markdown-it-highlightjs'))
.use(require('markdown-it-attrs'));
import axios from "axios";
export default {
    props: ['title', 'image', 'body', 'category', 'id'],
    data(){
        return{
            content: '',
        }
    },
    created(){
        this.content = md.render(this.body); 
     
    }
}
</script>

<style lang="scss">

    .horizontal{
        @include center;
        justify-content: space-evenly;
        padding: 2% 3.5%;
        position: relative;
        border-top: 1px solid black;
        width: 80vw;
        margin: 0 auto;

        @include respond(phone){
            margin: 0;
            width: 100%;
            padding: 0;
        }

        &__image-box{
     
            width: 15.38rem;
            height: 17.25rem;

            @include respond(phone){
                width: 12.5rem;
                height: 12rem;
            }

            & img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }

        &__info{    
            width:100%;
            padding-left: 2.5rem;

            @include respond(phone){
                padding-left: 0;
                margin-left: .5rem;
            }

            &-category{
                text-transform: uppercase;
                font-family: 'Muli-Light', sans-serif;
                font-weight: 300;
                text-align: center;
                letter-spacing: 1.7px;

                @include respond(phone){
                    font-size: .9rem !important;
                }
            }

            &-title{
                @include sub-titulo;
                margin: .7rem 0;

                @include respond(phone){
                    font-size: 1.3rem !important;
                }
            }

            &-body{
                overflow: hidden;
                text-overflow: ellipsis;
                display: -webkit-box;
                -webkit-line-clamp: 4; /* number of lines to show */
                -webkit-box-orient: vertical;
                font-family: 'Muli-Light', sans-serif;
                text-align: center;
                line-height: 1.8;

                @include respond(phone){
                    font-size: .9rem !important;
                }
            }

            &-btn{
                @include buttonArticle;
                margin: 1rem auto;

                @include respond(phone){
                    font-size: .8rem !important;
                }
                
                &::after{
                     @include line-bottom;
                     height: .5px;
                }
            }
        }
    }
</style>