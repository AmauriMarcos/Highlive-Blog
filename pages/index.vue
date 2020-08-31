<template>
  <div>
    <section id="hero">
       <TheHero></TheHero>
    </section>  

    <section id="white-articles">
      <div v-for='(article, i) in articles' :key='i'>
         <nuxt-link :to="`/${article.id}`" class="wrap-link">
            <div class="bloco-article">
              <h2>{{article.title}}</h2>
              <p>{{article.description}}</p>
              <button>Continuar lendo</button>
            </div>
          </nuxt-link>
      </div>   
    </section>

    <section id="cards">
        <div v-for="(card, i) in cards " :key='i'>
            <Cards :title='card.title' :category='card.categories[0].name' :image='card.image[0].name' :id='card.id'></Cards>
        </div>
    </section>

    <section id="newsletter">
        <Newsletter></Newsletter>
    </section>

    <section id="boxes">
      <div class="boxes-div">
         <div class="thebox thebox-1">
           <nuxt-link  tag="a" to="/posts" class="wrap-link">
              <p>Arquivos</p>
           </nuxt-link> 
        </div>

        <div class="thebox thebox-2">
            <p>Dicas</p>
        </div>

        <div class="thebox thebox-3">
          <nuxt-link  tag="a" to="/projeto-100" class="wrap-link">
            <p>Projeto 100</p>
          </nuxt-link> 
        </div>
      </div>      
    </section>

    <section id="horizontal-articles">
      <div v-for="(horizontal, i) in horizontals" :key="i" class="horizontal-box">
         <HorizontalArticle
            :title='horizontal.title'
            :image='horizontal.image[0].name'
            :body='horizontal.body'
            :category='horizontal.categories[0].name'
            :id='horizontal.id'
         ></HorizontalArticle>
      </div>
    </section>

  </div> 
</template>

<script>
  import axios from "axios";
  import HorizontalArticle from "../components/HorizontalArticle";
  import TheHero from "../components/TheHero";
  import Cards from "../components/Cards";
  import Newsletter from "../components/Newsletter";
  export default {
    components: {
      TheHero,
      Cards,
      Newsletter,
      HorizontalArticle
    },
    data(){
      return{
        articles: [],
        cards: [],
        horizontals: []
      }
    },
    async created(){
      const res = await axios.get("https://amauri-blog.herokuapp.com/posts")
      const request1 = res;
      const request2 = res;
      const request3 = res;

      const articles = request1.data.slice(0,1)
      this.articles  = articles

     request2.data.slice(3,6).map((card) =>{
          this.cards.push(card)
      })

      this.horizontals  = request3.data.slice(0,5)

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
          @include buttonArticle;

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
   .thebox{
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

   .thebox-1{
     background: url('https://images.unsplash.com/photo-1496181133206-80ce9b88a853?ixlib=rb-1.2.1&auto=format&fit=crop&w=1051&q=80');
     @include box;
   }
   .thebox-2{
     background: url('https://images.unsplash.com/photo-1535320903710-d993d3d77d29?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80');
     @include box;
   }
   .thebox-3{
     background: url('https://images.unsplash.com/photo-1517963628607-235ccdd5476c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1051&q=80');
     @include box;
   }

   #horizontal-articles{
     display: flex;
     flex-direction: column; 
     margin-top: 2%;
     
     &::after{
       @include line;
     }
   }

  
</style>