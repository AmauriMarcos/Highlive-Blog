<template>
    <div>
        <div class="projeto">
            <div class="projeto__call">
                <div class="projeto__call-esquerda">
                    <h1>Projeto <span class="cem">100</span> Dias</h1>
                </div>
                <div class="projeto__call-direita">
                    <p>A ideia surgiu para me motivar e quem sabe, te motivar também.
                         O objetivo é passar 100 dias comendo limpo, sem beber álcool e treinando regularmente. E aí ? Bora pro desafio também?
                    </p>
                </div>              
            </div>
        </div>

        <div class="pages-cards">
            <div v-for="(dia, i) in dias" :key="i">
                 <ProjetoCard  :id='dia.id' :title='dia.title' :image='dia.image[0].name' :category='category' :contador='dia.dia' ></ProjetoCard>
            </div>
        </div>  

    </div>
</template>

<script>
import ProjetoCard from "../../components/ProjetoCard";
import axios from "axios";
export default {
    components:{
        ProjetoCard
    },
    data(){
        return{
            dias: [],
            category: 'Projeto 100 Dias',
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/categories?name=Projeto-100")
        const posts = res.data;
        posts.map((post) =>{
            this.dias = post.posts;
        })

    }
}
</script>

<style lang="scss">
    @font-face {
        font-family: 'Higher Jump';
        src: url('~assets/fonts/Higher Jump.ttf') format('truetype');
        font-style: normal;
        font-weight: normal;      
    }   
    
    .projeto{
       height: 70vh;
       width: 100%;
       padding: 2% 9.5%;
       margin-top: 2rem;
       background: linear-gradient(to right, rgba(0,0,0,.5), rgba(0,0,0,.5)), url("https://images.unsplash.com/photo-1571902943202-507ec2618e8f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=968&q=80");
       background-size: cover;
       background-repeat: no-repeat;
       background-position: center;

     

       &__call{
           height: 100%;
           width: 100%;
           padding: 2.5rem;
           display: grid;
           grid-template-columns: repeat(3,1fr);
           align-items: center;
           justify-items: center;
           column-gap: 2rem;

           &-esquerda{
               grid-column: 1/3;

                 & h1{
                    font-family: 'Higher Jump';
                    font-size: 3rem;
                    text-align: center;
                    color: white;
                    transform: translateY(-4rem);
                }
           }

           &-direita{
               grid-column: 3/4;

                & p{
                    margin: 0 !important;
                    font-family: 'Muli-Light', sans-serif;
                    font-size: 1.5rem;
                    color: #fff;
                    background-color: rgba(197, 30, 37,.4); 
                    padding: 7rem 2rem;
                    padding-top: 8.3rem;
                    transform: translateY(-4.3rem);
                    
                }
           }        
           
       }

       .cem{
           color: rgba(0, 126, 255,.9);
           font-size: 4rem;
       }

    }

    .pages-cards{
        display: grid;
        padding: 2% 9.5%;
        gap: 1rem;
        grid-template-columns: repeat(auto-fit, minmax(345px, 1fr));
    }
</style>