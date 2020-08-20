<template>
    <div class="destaques">
        <div class="destaques__principal">
            <img :src="`${destaques[0].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[0].title}}</h1>
            </div>
        </div>
        <div class="destaques__cima">
            <img :src="`${destaques[1].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[1].title}}</h1>
            </div>
        </div>
        <div class="destaques__baixo">
            <img :src="`${destaques[2].image[0].name}`" alt="">
            <div class="white-box">
                <h1 class="white-box__title">{{destaques[2].title}}</h1>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            destaques: []
        }
    },
    async fetch(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
        const news = res.data;
        news.slice(-3).map((destaque) =>{
            this.destaques.push(destaque);
        })
    }
}
</script>

<style lang="scss">
    .destaques{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        padding: 2% 9.5%;
        gap: .5rem;

        &__principal{
            grid-column: 1/3;
            grid-row: 1/3;
            height: 60vh;
            position: relative;
            

            & img{
                @include imageOnGrid;
                
                
            }

            & .white-box{
                @include whiteBox;

                &__title{
                    font-family: 'Playfair Display', serif;
                    font-weight: 400;
                    font-size: 28px;
                    padding: 1.5rem 2.5rem;
                }
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

        
    }
</style>