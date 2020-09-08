<template>
    <div class="destaques">
        <div v-for="(destaque, i) in destaques" class="box" :class="{'full-height-box': i == 0}" :key="i" >
            <nuxt-link tag='a' :to="`/${destaque.id}`" class="wrap-link" >
                <img :src="`${destaque.image[0].name}`" alt="" class="box-img" @click='buttonClicked()'>
                <div class="white-box" @click='buttonClicked()'>
                     <h1 class="white-box__title">{{destaque.title}}</h1>
                </div>
            </nuxt-link>
        </div>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            destaques: [],
            
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        const data = res.data;
        this.destaques= data.slice(-3);     
    },
    methods: {
        buttonClicked(){
            this.$gtag('event', 'clicou_em_destaques', {
            'event_category': 'artigos',
            'event_label': 'Artigo em Destaques foi Clicado',
            'value': 1
            });
        }
    }
}
</script>

<style lang="scss">
    .wrap-link{
        text-decoration: none;
        color: $black;
    }

    .white-box{
        @include whiteBox;

        @include respond(phone){
            background: transparent;
        }

        &__title{
            @include sub-titulo;
            padding: 1rem 1.5rem;
            margin: 0;
            font-size: 1.5rem;
            width: 120%;
            transform: translateX(-1rem);
            background-color: $white;

            @include respond(phone){
                line-height: 1.3;
            }

            @include respond(phone){
                padding: .3rem .8rem;
            }

            @include respond(phone){
                font-size: 1.2rem
            }
        }
    }

    .box{
       width: 100% !important;
       height: 100% !important;
       margin: 0 !important;
       transform: translateX(-.24rem);
    }

    .box-img{
        height: 100%;
        object-fit: cover;
        width: 100%;
    }

    .full-height-box {
        grid-row: 1 / span 2;
        width: 100%;

        @include respond(phone){
            grid-column: 1/ span 2;
            grid-row: 1;
        }
        
    }
    .destaques{
        display: grid;
        grid-template-columns: 60% 40%;
        grid-template-rows: 250px 250px;
        grid-gap: 10px; /* OPTIONAL */
        padding: 2% 10%;

        @include respond(phone){
            grid-template-columns: 50% 50%;
            grid-template-rows: 250px;
            padding: 2% 5%;
            grid-gap: 7px;
        }
    }
</style>