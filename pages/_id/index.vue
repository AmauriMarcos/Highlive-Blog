<template>
    <div class="article">
        
        <div class="article__content">
            <div class="article__content-square"></div>
            <div class="article__content-image">              
                <img :src="`${url}`" alt="">
            </div>
            <div class="article__content-call">
                <p class="article__content-call--date">{{date}} </p>
                <h2>{{article.title}}</h2>
                <p class="article__content-call--paragraph">{{article.description}}</p>
            </div>  
            <div class="article__content-body">
               <p v-html="content">{{content}}</p>  
               <h2 class="comentario-titulo">Deixe um comentário</h2>
               <Comments class="comments__component" :id='article.id' ></Comments>     
            </div> 
                
        </div>

        <div class="article__bio">
            <div class="article__bio-intro">
                <p>E aí, tudo certo?</p>
            </div>
            
            <div class="article__bio-image">
                <img src="https://images.unsplash.com/photo-1518020382113-a7e8fc38eac9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=660&q=80" alt="">
            </div>
            <div class="article__bio-description">
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
            </div>   
            <h3 class="tag-title">Tags</h3> 
            <div class="article__bio-tags">
                <div v-for="(tag, i) in tags" :key="i">
                    <nuxt-link :to="`/relacionados/${tag.name}`" class="wrap-link">
                        <p class="tag">{{tag.name}}</p>
                    </nuxt-link>
                    
                </div>
            </div>  

            <div class="theSearch">
                <Search></Search>
            </div>
            
            <div class="space"></div>  
        </div>
    </div>
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

import Comments from "../../components/Comments";
import axios from "axios";
import Search from "../../components/Search";
export default {

    components: {
        Search,
        Comments
    },
    data(){
        return{
            article: [],
            url: '',
            tags: [],
            content: '',
            date: ''
        }
    },
    
    async created(){
        const res = await axios.get(`https://amauri-blog.herokuapp.com/posts?slug=${this.$route.params.id}`)
        this.article = res.data
        this.article.map((art) =>{
            this.url = art.image[0].name

            this.article = art

            const d = new Date(art.date)
            const ye = new Intl.DateTimeFormat('pt', { year: 'numeric' }).format(d)
            const mo = new Intl.DateTimeFormat('pt', { month: 'short' }).format(d)
            const da = new Intl.DateTimeFormat('pt', { day: '2-digit' }).format(d)
            this.date = `${da} ${mo} ${ye}`    

            this.content = md.render(art.body);  
        })
      /*   this.url = this.article.image[0].name */

       

        const result = await axios.get("https://amauri-blog.herokuapp.com/tags")
        this.tags = result.data

       
        
    },
    
}
</script>

<style lang="scss">
body{

    @include respond(phone){
        overflow-x: hidden;
    }
    
}
    @font-face {
        font-family: 'Muli-Light';
        src: url('~assets/fonts/Muli-Light.ttf') format('truetype');
        font-style: normal;
        font-weight: normal;      
    }


    .comentario-titulo{
        @include sub-titulo;
        transform: translateY(1rem);
    }
// BLOCO DE MARKDOWN //

    .blog-front{
        border-radius: 5px;
        width: 100%;

    }

    .grande{
        width: 100%;
        height: 90%;
    }

    .gif{
        transform: translateX(15rem);
        width: 20rem;
        height: 20rem;
    }

    .projeto-link{
        font-weight: bold;
        text-decoration: none;
        color: rgba(0, 126, 255,.7);
        cursor: pointer;
        outline: none;
    }

    .meu-gif{
        width: 30rem;
        height: 17rem;
        @include center;

        @include respond(phone){
            width: 100%;
        }
    }

    .agua{
        width: 35rem !important;
    }
  // BLOCO DE MARKDOWN //
    .article{
        padding: 2% 9.5%;
        display: grid;
        grid-template-columns: repeat(4,1fr);

        @include respond(phone){
     /*        padding: 2% 9% !important; */
            @include center;
            flex-direction: column;
        }      

        &__content{
            grid-column: 1/4;
            grid-row: 1/2;
            height: 60vh;
            display: grid;
            grid-template-columns: repeat(3, 1fr);

        @include respond(phone){
            grid-column: 1/-1;
            height: 100%;
        }
            
            &-square{
                width: 15rem;
                height: 15rem;
                background-color: rgba(0, 126, 255,.4);
                grid-column: 1/2;
                grid-row: 2/3;
                transform: translate(-1.5rem, 1.5rem);
                align-self: flex-end;
                z-index: 1;

                @include respond(phone){
                    width: 8rem;
                    height: 8rem;
                    transform: translate(-.7rem, .7rem);
                    display: none;
                }
                
            }

            &-image{
                width: 38rem;
                height: 30rem;
                grid-column: 1/3;
                grid-row: 2/3;
                z-index: 10;

                @include respond(phone){
                    width: 100%;
                    height: 16rem;
                    position: relative;
                }
               

                & img{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                }
            }

            &-call{
                grid-column: 3/4;
                grid-row: 2/3;
                background-color: rgb(211, 233, 255);
                align-self: flex-start;
                padding: 2rem;
                transform: translate(-2rem, 12rem);
                z-index: 15;
                width: 30rem;

                @include respond(phone){
                    grid-column: 1/2;
                    grid-row: 3/4;
                    transform: translate(2rem, -5rem);
                    width: 25rem;
                    height: 23rem;
                    padding: 3rem;
                    background-color: transparent;
                }

                &--date{
                    font-size: .8rem;
                    text-transform: uppercase;
                    background-color: rgba(0, 126, 255,.2);
                    width: 30%;
                    padding: .5rem 1rem;
                    color: $white;

                    @include respond(phone){
                        font-size: .6rem !important;
                        padding: 0 !important;
                        transform: translate(-3rem, -15rem) !important;
                        padding: .3rem .5rem !important;
                        color: #666;
                        font-family: 'Muli-Light', sans-serif;
                        background-color:rgb(211, 233, 255);
                        text-align: center;
                        font-weight: bold;
                    }
                }

                & h2{
                    
                    @include sub-titulo;

                    @include respond(phone){
                        font-size: 1.3rem !important;
                        background-color: $white;
                        transform: translate(-2rem, -4rem);
                        z-index: 100;
                        position: relative;
                        box-shadow: 1px 1px 3px rgba(0,0,0.2);
                        padding: .4rem .5rem !important;
                    }
                }

                &--paragraph{
                    @include paragrafo(left);
                    font-family: 'Muli-Light', sans-serif;

                    @include respond(phone){
                        font-size: .9rem !important;
                        background-color: rgb(211, 233, 255);
                        transform: translate(2.3rem, -12rem);
                        padding: 2rem;
                        z-index: 50;
                        display: none;
                
                    }
                }

            }

            &-body{
                grid-column: 1/-1;
                grid-row: 3/4;
                margin-top: 5rem;
                padding-right: 3rem;
                font-family: 'Muli-Light', sans-serif;
                line-height: 32px;
                font-size: 20px;
           /*      color: #8e8f88; */
                color: #666;

                letter-spacing: .3px;
                /*  border-right: 1px solid black; */

                @include respond(phone){
                    padding: 0 2rem !important;
                    font-size: 18px;
                    margin: 4.5rem 0 0 0 !important;
                    /* transform: translateY(6rem); */
                }

            }

        }

        &__bio{
            grid-column: 4/5;
            grid-row: 1/2;
            border-left: 1px solid black;
            border-right: 1px solid black;
            display: flex;
            flex-direction: column;
          /*   justify-content: center; */
           /*  align-items: center; */

            @include respond(phone){
                display: none;
            }

            &-intro{
                 align-self: center;

                 & p {
                    font-family: 'Muli-Light', sans-serif;
                    font-weight: 300;
                    margin-bottom: 1rem;
                    text-transform: uppercase;
                    letter-spacing: .2rem;
        
                 }
            }
        
            &-image{
                width: 14rem;
                height: 21rem;
                align-self: center;

                & img{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                }
            }

            &-description{
                margin-top: 1rem;
                padding: 1rem 1.5rem;
                font-size: .9rem;
                line-height: 1.5rem;


                & p {
                    font-family: 'Muli-Light', sans-serif;
                    font-weight: 400;
                    text-align: center;
                    
                }
            }

            &-tags{
                display: grid;
                gap: .8rem;
                grid-template-columns: repeat(auto-fit, minmax(90px, 1fr));
                color: rgb(0, 0, 0);
                font-family: 'Playfair Display', serif;
                font-weight: 400;
                text-align: center;
                text-transform: uppercase;
                padding: .5rem;
               
               
            }
        }
    }
    

    .tag{
        background-color: #f6f6f2;
        font-size: .9rem;
        width: 100%;
        padding: .5rem 1rem;
        margin: 0 !important;
    }
    .tag-title{
        font-family: 'Playfair Display', serif;
        font-weight: 700;
        text-align: center;
        margin: 1rem 0;
    }

  /*   .strapi-content{
        font-family: 'Open Sans', sans-serif;
        line-height: 1.7rem;
        font-size: 1.1rem;
    } */

    .theSearch{
        align-self: center;
        border-top: 1px solid black;
        border-bottom: 1px solid black;
        width: 100%;
        margin-top: 2rem;
    }

    p{
        margin: 1.5rem 0;          
    }

   
</style>