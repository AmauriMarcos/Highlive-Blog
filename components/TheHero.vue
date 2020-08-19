<template>
    <div>
        <div class="destaques">
            <div class="destaques__principal">
               <!--  <img :src="`${this.destaques[1].image[0].name}`" alt=""> -->
                <img src="https://images.unsplash.com/photo-1498262257252-c282316270bc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjExMDk0fQ&auto=format&fit=crop&w=500&q=60" alt="">
                <div class="white-box">
                    <h1 class="white-box__title">{{destaques[0].title}}</h1>
                </div>
            </div>
            <div class="destaques__cima">
                <img src="https://images.unsplash.com/photo-1531772290195-0d46f4200951?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=701&q=80" alt="">
                <div class="white-box">
                    <h1 class="white-box__title">{{destaques[1].title}}</h1>
                </div>
            </div>
            <div class="destaques__baixo">
                <img src="https://images.unsplash.com/photo-1505935428862-770b6f24f629?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1047&q=80" alt="">
                <div class="white-box">
                    <h1 class="white-box__title">{{destaques[2].title}}</h1>
                </div>
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
        const news = res.data.slice(-3)
        this.destaques = news
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
                    font-size: 18px;
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
                    font-size:18px;
                    padding: 1rem 2rem;
                }
            }
        }

        
    }
</style>