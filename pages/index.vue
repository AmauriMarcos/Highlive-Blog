<template>
  <div>
    <section id="hero">
       <TheHero></TheHero>
    </section>  

    <section id="white-articles">
      <div v-for='(article, i) in articles' :key='i'>
          <div class="bloco-article">
             <h2>{{article.title}}</h2>
             <p>{{article.description}}</p>
             <button>Saiba mais</button>
          </div>
      </div>
    </section>

    <section id="cards">
        <div v-for="(card, i) in cards " :key='i'>
            <Cards :title='card.title' :category='card.categories[0].name' :image='card.image[0].name'></Cards>
        </div>
    </section>

    <section id="newsletter">
        <Newsletter></Newsletter>
    </section>

    <section id="boxes">
      <div class="boxes-div">
         <div class="box box-1">
            <p>Arquivos</p>
        </div>
        <div class="box box-2">
            <p>Dicas</p>
        </div>
        <div class="box box-3">
            <p>Projeto 100</p>
        </div>
      </div>      
    </section>

  </div> 
</template>

<script>
import axios from "axios";
import TheHero from "../components/TheHero";
import Cards from "../components/Cards";
import Newsletter from "../components/Newsletter";
export default {
  components: {
    TheHero,
    Cards,
    Newsletter
  },
  data(){
    return{
      articles: [],
      cards: []
    }
  },
  async created(){
    const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
    const articles = res.data.slice(0,1)
    this.articles  = articles

    const result   = await axios.get("https://amauri-blog.herokuapp.com/posts")
    const myCards  = result.data;
    myCards.slice(1,4).map((card) =>{
        this.cards.push(card)
    })
  }

}
</script>
<style lang="scss">
   #white-articles{
     display: grid;
     grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
     gap: 1rem;
     padding: 2% 9.5%;
     position: relative;

     &::before{
       @include line;
       position: absolute;
       top: 1rem;
       width: 80vw;
       left: 8.8rem;
     }

     &::after{
        @include line;
        position: absolute;
        bottom: 1rem;
        width: 80vw;
        left: 8.8rem;
     }
     
   }

   .bloco-article{
     width: 100%;
     height: 100%;
     @include center;
     padding: 2rem .5rem;
     flex-direction: column;


        & h2{
          @include sub-titulo;
        }

        & p{
          @include paragrafo(center);
          
        }

        & button{
          border: none;
          font-family: 'Open Sans', sans-serif;
          padding: .2rem 0;
          font-weight: 300;
          text-transform: uppercase;
          display: flex;
          justify-self: center;
          outline: none;
          position: relative;
          font-size: .9rem;
          margin-top: 1rem;

          &::after{
             @include line-bottom;            
          }
        }
   }

   #cards{
     display: grid;
     padding: 2% 9.5%;
     gap: 1rem;
     grid-template-columns: repeat(auto-fit, minmax(345px, 1fr));
   }

   #newsletter{
     padding: 0 9.5% 2% 9.5%;

        &::before{
          @include line;
        }

        &::after{
          @include line;
          height: .5px;
        }
   }

   #boxes{
     display: grid;
     grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
     padding: 2% 9.5%;
     gap: 2rem;
   }

  .boxes-div{
    @include center;
    justify-content: space-around;
  }
   .box{
     width: 370px;
     height: 260px;
     display: inline-block;
     position: relative;

     & p{
       @include whiteBox;
       @include sub-titulo;
       padding: 0.7rem 1rem;
       width: 60%;
       text-transform: uppercase;
     }
   }

   .box-1{
     background: url('https://images.unsplash.com/photo-1496181133206-80ce9b88a853?ixlib=rb-1.2.1&auto=format&fit=crop&w=1051&q=80');
     @include box;
   }
   .box-2{
     background: url('https://images.unsplash.com/photo-1535320903710-d993d3d77d29?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80');
     @include box;
   }
   .box-3{
     background: url('https://images.unsplash.com/photo-1517963628607-235ccdd5476c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1051&q=80');
     @include box;
   }
</style>