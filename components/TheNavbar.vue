<template>
    <div class="header">
       
       <div class="header__brand">
           <!--  <nuxt-link to='/' class="wrap-link"> -->
                <a href="/" class="header__brand--title">High<span>live</span></a>
          <!--   </nuxt-link> -->
        </div>
       
         <div class='line'></div>


         <div class="mobile-menu">
             <input type="checkbox"  id="name" name="name" class="mobile-menu__name">
             <label for="name" class="mobile-menu__name"></label>

             <nav class="mobile-menu__nav">
                 <ul class="mobile-menu__nav-list" >      
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/" class="wrap-link header__link active-link exact-active-link" >Home</nuxt-link> 
                    </li> 
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/games" class="wrap-link header__link active-link exact-active-link" >Games</nuxt-link> 
                    </li> 
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/programação" class="wrap-link header__link active-link exact-active-link" >Programação</nuxt-link> 
                    </li> 
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/cotidiano" class="wrap-link header__link active-link exact-active-link" >Cotidiano</nuxt-link> 
                    </li> 
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/projeto-100" class="wrap-link header__link active-link exact-active-link" >Projeto-100</nuxt-link> 
                    </li> 
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/sobre" class="wrap-link header__link active-link exact-active-link">Sobre</nuxt-link> 
                    </li>  
                    <li class="mobile-menu__nav-item">
                        <nuxt-link tag='a' to="/contato" class="wrap-link header__link active-link exact-active-link">Contato</nuxt-link> 
                    </li>   
                </ul>
             </nav>
         </div>


         <ul class="header__list" >      
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

export default {
    data(){
        return{
            show: 'false'
        }
    },

}
</script>
<style lang="scss">
    .show{
        display: block;
    }
    .mobile-menu{
        display: none;
          
        @include respond(phone){
            @include center;
            display: block;
            width: 90vw;
            margin: 1rem 0 !important;
            transition: all .8s ease-in;                  
        }

        &__nav{
            background-color: rgba(0, 0, 0,.85);
            width: 51%;
            position: fixed;
            top: 0;
            right: 0;
            height: 100%;
            z-index: 100;
            transform: translateX(20rem);
             transition: all .2s ease-in-out;
           

            &-list{
                list-style: none;
                position: relative;
                 margin-top: 10rem;
                
            }

            &-item{
                margin-left: 2rem;
                margin-bottom: 1rem;
                font-family: 'Muli-Light', sans-serif;
                /*  font-family: 'Raleway', sans-serif; */
                font-weight: 300;
                text-transform: uppercase;
                font-size: 1rem;
                font-weight: bold;
               
               & a{
                    color: $white;
               }

            }
        }

        &__name{
            @include center;
            position: absolute;
            top: 3.5rem;
            right: 3rem;
            z-index: 500;
            height: 4px;
            border: 3px;
            width: 10%;
            display: inline-block;
            background-color: rgba(0, 126, 255,.7);

            &::before{
                content: '';
                background-color: rgba(0, 126, 255,.7);
                width: 85%;
                height: 4px;
                display: inline-block;   

            }

            &::after{

            }
        }
    }

    input[type='checkbox']{
        display: none;
    }

    input[type='checkbox']:checked ~ nav{
        transform: translateX(0);
    }

    
    .nuxt-link-active{
        color: $black !important;
        position: relative;
        z-index: 5;

        @include respond(phone){
             color:rgba(99, 133, 167, 0.7) !important;
            
         }

    }
   .nuxt-link-exact-active{
        color:rgba(0, 126, 255,.7) !important;    
         font-weight: bold;

         /* @include respond(phone){
             color: $white !important;
         } */
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

        @include respond(phone){
           box-shadow: 1px 1px 7px rgba(0, 0, 0,.2); 
           margin-bottom: 1.5rem;
        }

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
                font-size: 3rem;
                transform: translate(-7rem, 1rem);
            }
        }

        span{
            
            font-size: 7rem;
            position: relative;

             @include respond(phone){
                font-size: 4.5rem;
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
                left: -.6rem;

                @include respond(phone){
                     height: 60px;
                     width: 60px;
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

        @include respond(phone){
           display: none;
        }
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