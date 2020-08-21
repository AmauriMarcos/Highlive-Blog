<template>
    <div class="header">
       <div class="header__brand">
            <h1 class="header__brand--title">High<span>live</span></h1>
        </div>
         <div class='line'></div>
         <ul class="header__list" >     
             <li class="header__item" v-for='(category, i) in categories' :key='i'>
                <a href="#" class="header__link">{{category.name}}</a>
            </li>    
            <li class="header__item">
                <a href="#" class="header__link">Sobre</a>
            </li>   
            <li class="header__item">
                <a href="#" class="header__link">Contato</a>
            </li>   
        </ul>
    </div>
</template>
<script>
import axios from "axios";
export default {
    data(){
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
    }
}
</script>
<style lang="scss">
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
           
        }

        span{
            
            font-size: 7rem;
             position: relative;

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
       
    }

    .line{
        @include line;
        position: absolute;
        width: 80vw;
        top: 9.3rem;
    }

    &__item{
        margin-right: 1rem;
        font-family: 'Open Sans', sans-serif;
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