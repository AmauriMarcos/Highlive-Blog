<template>
    <div class="header">
       
       <div class="header__brand">
           <!--  <nuxt-link to='/' class="wrap-link"> -->
                <a href="/" class="header__brand--title">High<span>live</span></a>
          <!--   </nuxt-link> -->
        </div>
       
         <div class='line'></div>
         <ul class="header__list" >     
             <!-- <li class="header__item" v-for='(category, i) in categories' :key='i'>
                <nuxt-link :to="`/${category.name}`" class="wrap-link"> 
                    <a href="#" class="header__link">{{category.name}}</a>
                </nuxt-link>  
            </li> -->   
            <li class="header__item">
                <nuxt-link tag='a' to="/" class="wrap-link header__link active-link exact-active-link" >Home</nuxt-link> 
            </li> 
             <li class="header__item">
                <nuxt-link tag='a' to="/games" class="wrap-link header__link active-link exact-active-link" >Games</nuxt-link> 
            </li> 
             <li class="header__item">
                <nuxt-link tag='a' to="/programação" class="wrap-link header__link active-link exact-active-link" >Programação</nuxt-link> 
            </li> 
             <li class="header__item">
                <nuxt-link tag='a' to="/cotidiano" class="wrap-link header__link active-link exact-active-link" >Cotidiano</nuxt-link> 
            </li> 
             <li class="header__item">
                <nuxt-link tag='a' to="/projeto-100" class="wrap-link header__link active-link exact-active-link" >Projeto-100</nuxt-link> 
            </li> 
             <li class="header__item">
                <nuxt-link tag='a' to="/sobre" class="wrap-link header__link active-link exact-active-link">Sobre</nuxt-link> 
            </li>  
            <li class="header__item">
                <nuxt-link tag='a' to="/contato" class="wrap-link header__link active-link exact-active-link">Contato</nuxt-link> 
            </li>   
        </ul>
    </div>
</template>
<script> 
/* import axios from "axios"; */
export default {
/*     data(){
        return{
            categories: []
        }
    },
    async created(){
        const res = await axios.get("https://amauri-blog.herokuapp.com/categories")
        const myData = res.data;
        myData.map((data) =>{
            this.categories.push(data)
        })
    } */
}
</script>
<style lang="scss">
    .nuxt-link-active{
        color: $black !important;
        position: relative;
        z-index: 5;

    }
   .nuxt-link-exact-active{
        color:rgba(0, 126, 255,.7) !important;    
         font-weight: bold;
    }

    @font-face {
        font-family: 'Miya Wayne';
        src: url('~assets/fonts/Miya Wayne.ttf') format('truetype');
        font-style: normal;
        font-weight: normal;      
    }   

    .header{
        @include center;
        flex-direction: column;

        &__brand{
        display: flex;
        justify-content: center;
        align-items: center;
    

        &--title{
            font-family: 'Miya Wayne';
            font-size: 5rem;
            text-align: center;
            color: $black !important;
            text-decoration: none;
            font-weight: bold;
            cursor: pointer;

            @include respond(phone){
                font-size: 4rem;
            }
        }

        span{
            
            font-size: 7rem;
            position: relative;

             @include respond(phone){
                font-size: 6rem;
            }

            &:before{
                content: "";
                background-color: rgba(0, 126, 255,.4);
                height: 90px;
                width: 90px;
                border-radius: 50%;
                display: inline-block;
                position: absolute;
                top: .3rem;
                left: -.5rem;

                @include respond(phone){
                     height: 75px;
                     width: 75px;
                 }
            }           
        }      
    }

    &__list{
        @include center;
        list-style: none;
        margin-top: 2rem;
        border-top: 1px solid black;
        border-bottom: 1px solid black;
        justify-content: space-around;
        width: 80vw;
        padding: 1rem 2rem;  
        @include respond(phone){
            display: none;
        }
       
    }

    .line{
        @include line;
        position: absolute;
        width: 80vw;
        top: 9.3rem;
    }

    &__item{
        margin-right: 1rem;
       font-family: 'Muli-Light', sans-serif;
       /*  font-family: 'Raleway', sans-serif; */
       font-weight: 300;
       text-transform: uppercase;
       font-size: 1rem;
       position: relative;

       
    }

    &__link{
        text-decoration: none;
        color: $black;
    }

    &__icons{
       
       & a{
            text-decoration: none;
            color: $black;
            font-family: 'Open Sans', sans-serif;
            font-weight: 700;
       }
    }

}

   
    
</style>