<template>
    <div class="article">
        
        <div class="article__content">
            <div class="article__content-square"></div>
            <div class="article__content-image">              
                <img :src="`${url}`" alt="">
            </div>
            <div class="article__content-call">
                <h2>{{article.title}}</h2>
                <p>{{article.description}}</p>
            </div>  
            <div class="article__content-body">
               <p v-html="content">{{content}}</p>     
               <h2 class="comentario-titulo">Deixe um comentário</h2>     
                <div class="fb-comments" data-href="https://highlive.netlify.app/" data-numposts="5" data-width="955"></div> 
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
                    <p class="tag">{{tag.name}}</p>
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


import axios from "axios";
import Search from "../../components/Search";
export default {

    components: {
        Search
    },
    data(){
        return{
            article: [],
            url: '',
            tags: [],
            content: '',
            theID: this.$route.params.id
        }
    },
    mounted(){
        this.init()    
    },
    methods: {
        init (){
        if (window.FB) {
            window.FB.init({
                appId      : process.env.APP_ID,
                status     : true,
                xfbml      : true,
                version    : 'v3.3'
            })
        }
    }
    },
    async created(){
        const res = await axios.get(`https://amauri-blog.herokuapp.com/posts/${this.$route.params.id}`)
        this.article = res.data
        this.url = this.article.image[0].name

        const result = await axios.get("https://amauri-blog.herokuapp.com/tags")
        this.tags = result.data

         this.content = md.render(res.data.body);  
    },
    
}
</script>

<style lang="scss">
    .comentario-titulo{
        @include sub-titulo;
        transform: translateY(1rem);
    }
    .agua{
        width: 35rem !important;
    }
  
    .article{
        padding: 2% 9.5%;
        display: grid;
        grid-template-columns: repeat(4,1fr);
        
/* 
        &__body{
            grid-column: 1/4;
            grid-row: 1/2;
            transform: translateY(35rem);
            padding-right: 5rem;
            font-family: 'Open Sans', sans-serif;
            line-height: 1.7rem;
            font-size: 1.1rem;
            align-self: flex-end;
        } */

        &__content{
            grid-column: 1/4;
            grid-row: 1/2;
            height: 60vh;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
           
           

            &-square{
                width: 15rem;
                height: 15rem;
                background-color: rgba(0, 126, 255,.4);
                grid-column: 1/2;
                grid-row: 2/3;
                transform: translate(-1.5rem, 1.5rem);
                align-self: flex-end;
                z-index: 1;
                
            }

            &-image{
                width: 38rem;
                height: 30rem;
                grid-column: 1/3;
                grid-row: 2/3;
                z-index: 10;
               

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

                & h2{
                    
                    @include sub-titulo;
                }

                & p{
                    @include paragrafo(left);
                }

            }

            &-body{
                grid-column: 1/-1;
                grid-row: 3/4;
                margin-top: 5rem;
                padding-right: 3rem;
                font-family: 'Open Sans', sans-serif;
                line-height: 1.7rem;
                font-size: 1.1rem;
                /*  border-right: 1px solid black; */

            }

        }

        &__bio{
            grid-column: 4/5;
            grid-row: 1/2;
            border-left: 1px solid black;
            display: flex;
            flex-direction: column;
          /*   justify-content: center; */
           /*  align-items: center; */

            &-intro{
                 align-self: center;

                 & p {
                    font-family: 'Open Sans', sans-serif;
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
                    font-family: 'Playfair Display', serif;
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
        margin-left: 1rem;
        margin-top: 2rem;
    }

    p{
        margin: 1.5rem 0;          
    }

  
    .space{
        height: 800px;
    }

   
</style>