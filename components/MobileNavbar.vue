<template>
    <div>
        <div class="container-mobile">
            <nav class="navbar">
                <div class="hamburger-menu">
                    <div class="line line-1"></div>
                    <div class="line line-2"></div>
                    <div class="line line-3"></div>
                </div>

                <ul class="nav-list">
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/" class="wrap-link nav-link active-link exact-active-link" >Home</nuxt-link> 
                    </li> 
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/games" class="wrap-link nav-link active-link exact-active-link" >Games</nuxt-link> 
                    </li> 
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/programação" class="wrap-link nav-link active-link exact-active-link" >Programação</nuxt-link> 
                    </li> 
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/cotidiano" class="wrap-link nav-link active-link exact-active-link" >Cotidiano</nuxt-link> 
                    </li> 
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/projeto-100" class="wrap-link nav-link active-link exact-active-link" >Projeto-100</nuxt-link> 
                    </li> 
                    <li class="nav-item">
                        <nuxt-link @click.native='linkClicked()' tag='a' to="/sobre" class="wrap-link nav-link active-link exact-active-link">Sobre</nuxt-link> 
                    </li>  
                    <li class="nav-item">
                        <nuxt-link tag='a' to="/contato" class="wrap-link nav-link active-link exact-active-link">Contato</nuxt-link> 
                    </li> 
                </ul>

            </nav>
        </div>
    </div>
</template>

<script>
export default {
    methods:{
        linkClicked(){
             this.$gtag('event', 'clicou_em_sobre', {
                'event_category': 'sobre',
                'event_label': 'Pagina sobre foi visitada',
                'value': 1
            });
        }
    },
    mounted(){
        const menuIcon = document.querySelector(".hamburger-menu");
        const navbar = document.querySelector(".navbar");


        menuIcon.addEventListener("click", () =>{
            navbar.classList.toggle("change")
        })

        window.addEventListener('click', function(e){
            
            if (document.querySelector('.navbar').contains(e.target)){
                navbar.classList.add("change")
            } else{
                navbar.classList.remove("change")
            }
        })
    }
}
</script>
<style lang="scss">
    .container-mobile{
        display: none;

        @include respond(phone){
            display: block !important;
            width: 100%;
            height: 100%;
            background-color: blueviolet;
        }

    }

    .hamburger-menu{
        width: 35px;
        height: 30px;
        position: fixed;
        top: 50px;
        right: 50px;
        cursor: pointer;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
    }

    .line{
        height: 3px;
        width: 100%;
        background-color: rgb(0, 0, 0);
        transition: all .8s;
    }


    .change .line-1{
        transform: rotateZ(-405deg) translate(-8px, 6px);
    }

    .change .line-2{
        opacity: 0;
    }

    .change .line-3{
        transform: rotateZ(405deg) translate(-8px, -6px);
    }

    .navbar{
        width: 260px;
        height: 100%;
        background-color:rgb(0, 128, 255) ;
        position: fixed;
        top: 0;
        right: -300px;
        z-index: 1000;
        @include center;
        border-radius: 45% 0 0 50%;
        transition: right .8s cubic-bezier(.32,2,.55,.27);

    }

    
    .change{
        right: 0;
    }

    .nav-list{
        list-style: none;
        text-align: right;
    }

    .nav-item{
        margin: 25px;

        @include respond(phone){
            color: black;
            font-weight: bold;
        }
        
    }

    .nav-link{
       color: $white;
       font-family: 'Muli-Light', sans-serif;
       letter-spacing: 1.2px;
       text-transform: uppercase;
    }


</style>