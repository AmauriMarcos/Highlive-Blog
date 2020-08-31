<template>
    <div class="destaques">
        <div v-for="(destaque, i) in destaques" class="box" :class="{'full-height-box': i == 0}" :key="i">
            <nuxt-link tag='a' :to="`/${destaque.id}`" class="wrap-link">
                <img :src="`${destaque.image[0].name}`" alt="" class="box-img">
                <div class="white-box">
                     <h1 class="white-box__title">{{destaque.title}}</h1>
                </div>
            </nuxt-link>
        </div>
        <!-- <div class="destaques__principal">
            <nuxt-link tag="a" :to='`/${destaques[0].id}`' class="wrap-link">
            <img :src="`${destaques[0].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[0].title}}</h1>
            </div>
            </nuxt-link>
            </div>
        <div class="destaques__cima">
            <nuxt-link tag="a" :to='`/${destaques[1].id}`' class="wrap-link">
            <img :src="`${destaques[1].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[1].title}}</h1>
            </div>
            </nuxt-link>

        </div>
        <div class="destaques__baixo">
            <nuxt-link tag="a" :to='`/${destaques[2].id}`' class="wrap-link">
            <img :src="`${destaques[2].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[2].title}}</h1>
            </div>
            </nuxt-link>

        </div> -->
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
    /* async fetch(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        const news = res.data;
        
        news.slice(-3).map((destaque) =>{
            this.destaques.push(destaque);
            const firstID = this.destaques[0].id;
            const secondID = this.destaques[1].id;
            const thirdID = this.destaques[2].id;

            console.log(firstID, secondID, thirdID);
        })
    }, */
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        const data = res.data;
        this.destaques= data.slice(-3);     
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
    

        &__title{
            @include sub-titulo;
            padding: 1rem 1.5rem;
            margin: 0;
            font-size: 1.5rem;
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
        
    }
    .destaques{
        display: grid;
        grid-template-columns: 60% 40%;
        grid-template-rows: 250px 250px;
        grid-gap: 10px; /* OPTIONAL */
        padding: 2% 10%;
    }
        /* &__principal{
            grid-column: 1/3;
            grid-row: 1/3;
            height: 60vh;
            position: relative;
            

            & img{
                @include imageOnGrid;               
            }

            
    
        }

        &__cima{
            grid-column: 3/4;
            grid-row: 1/2;
            position: relative;

            & img{
                @include imageOnGrid;
            }

            & .white-box{
                @include whiteBox;

                &__title{
                    font-family: 'Playfair Display', serif;
                    font-weight: 400;
                    font-size: 1.3rem;
                    padding: 1rem 2rem;
                }
            }
        }

        &__baixo{   
            grid-column: 3/4;
            grid-row: 2/3;
            position: relative;

            & img{
                @include imageOnGrid;
            }

            & .white-box{
                @include whiteBox;

                &__title{
                    font-family: 'Playfair Display', serif;
                    font-weight: 400;
                    font-size: 1.3rem;
                    padding: 1rem 2rem;
                }
            }
        }

        
    } */
</style>