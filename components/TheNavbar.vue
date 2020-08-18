<template>
    <header>
        <div class="brand">
            <h1 class="brand__title">Konversa</h1>
        </div>
        <navbar class="navbar">
            <ul class="navbar__list">
                <li class="navbar__item">item</li>
                <li class="navbar__item">item</li>
                <li class="navbar__item">item</li>
                <li class="navbar__item">item</li>
            </ul>
            <div class="navbar__icons">
                <p>icons</p>
                <p>icons</p>
            </div>
            <div class="navbar__search">
                <p>search</p>
            </div>
        </navbar>
    </header>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    @font-face {
    font-family: 'Nakone';
    src: url('~assets/fonts/Nakone.ttf') format('truetype');
    font-style: normal;
    font-weight: normal;      
}
    header{
        padding: 0 5% ;
    }
    header::after{
        @include line(1.5px, 1rem 0);
    }

    header::before{
        @include line(1px, 1rem 0);
        transform: translateY(11.4rem);
    }
    .brand{
        text-align: center;

        &__title{
            color: $primary-color;
            font-size: 6.5rem;
            font-family: 'Nakone';
            
        }
    }

    .navbar{
        @include center;
       /*  font-family: 'Libre Baskerville', serif; */
        font-family: 'Nunito', sans-serif;

     /*    &::after{
            content: "";
            height: 2px;
            background-color: $black;
            display: block;
            width: 100%;
        } */
        
        &__list{
            @include center;
            list-style: none;
        }

        &__item{
            margin-right: 1.5rem;
        }

        &__icons{
            @include center;
            
            & p {
                margin-right: 1.5rem;
            }
        }

        &__search{

        }
    }
</style>