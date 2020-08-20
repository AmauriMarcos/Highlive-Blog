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

  </div> 
</template>

<script>
import axios from "axios";
import TheHero from "../components/TheHero";
import Cards from "../components/Cards";
export default {
  components: {
    TheHero,
    Cards
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
</style>