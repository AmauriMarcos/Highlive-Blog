<template>
    <div class="header">
       <div class="header__brand">
            <h1 class="header__brand--title">High<span>live</span></h1>
        </div>
         <ul class="header__list">
             <div class='line'></div>
             <li class="header__item">
                <a href="#" class="header__link">Home</a>
            </li>
            <li class="header__item">
                <a href="#" class="header__link">Tecnologia</a>
            </li>
            <li class="header__item">
                <a href="#" class="header__link">Estilo de Vida</a>
            </li>
            <li class="header__item">
                <a href="#" class="header__link">Cotidiano</a>
            </li>
            <li class="header__item">
                <a href="#" class="header__link">Games</a>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    
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