<template>
    <div class="about">
        <div class="about__gallery">
            <div class="about__gallery--1">

            </div>
            <div class="about__gallery--2">
                
            </div>
            <div class="about__gallery--3">
                
            </div>
            <div class="about__gallery--4">
                
            </div>
            <div class="about__gallery--5">
                
            </div>
            <div class="about__gallery--6">
                
            </div>
            <div class="about__gallery--7">
                
            </div>
        </div>
        <div class="about__text">
            <div class="about__text-cima">
                <h2 class="about__text-cima--title">Sobre Mim</h2>
                <p class="about__text-cima--text">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rem qui eos iure ullam, dolore, nam magnam nemo at impedit cum, voluptatem debitis ipsa enim sit similique autem expedita distinctio dolores! Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi ducimus beatae aperiam nihil quas odit obcaecati maxime assumenda laboriosam, quasi impedit vitae itaque dolore ea labore voluptatem molestias culpa neque?</p>
            </div>
    
            
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss">
    .about{
        padding: 2% 9.5%;
        height: 100%;
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        justify-items: center;
        gap: 3rem;

        padding: 2% 7%;

        &__gallery{
            grid-column: 1/4;
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            grid-template-rows: repeat(12,1fr);
            gap: .7rem;
            width: 100%;
            height: 100%;

            @include respond(phone){
                grid-column: 1/-1;
                grid-row: 1/2;
                gap: 1rem;
            }

            &--1{
                grid-column: 1/6;
                grid-row: 1/6;           
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1491438590914-bc09fcaaf77a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--2{
                grid-column: 6/9;
                grid-row: 1/4;             
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1516314800700-e3760ce78970?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--3{
                grid-column: 9/-1;
                grid-row: 1/4;             
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1489710437720-ebb67ec84dd2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--4{
                grid-column: 1/6;
                grid-row: 6/-1;           
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1575037614876-c38a4d44f5b8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--5{
                grid-column: 6/-1;
                grid-row: 4/8;           
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1534665482403-a909d0d97c67?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--6{
                grid-column: 6/10;
                grid-row: 8/-1;           
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1530021694813-ac7bbbf6bb2f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=635&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
            &--7{
                grid-column: 10/-1;
                grid-row: 8/-1;           
                background: linear-gradient(to right, rgba(255,255,255,.2), rgba(255,255,255,.2)),url("https://images.unsplash.com/photo-1486572788966-cfd3df1f5b42?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1052&q=80");
                background-position: center;
                background-size: cover;
                background-repeat: no-repeat;
            }
        }

        &__text{
            grid-column: 4/-1;
            display: grid;
            grid-template-columns: repeat(4,1fr);
            column-gap: 2rem;

            @include respond(phone){
                grid-column: 1/-1;
                grid-row: 2/3;
            }

            &-cima{
                grid-column: 1/-1;
                grid-row: 1/2;

                &--title{
                    @include sub-titulo;
                    font-size: 2rem;
                    
                }

                &--text{
                    font-family: 'Muli-Light', sans-serif;
                    line-height: 25px;
                    font-size: 15px;
                    color: #8e8f88;
                    color: #666;
                }
            }

            &-esquerda{
                grid-column: 1/3;
                grid-row: 2/3;

                &--title{
                    @include sub-titulo;
                }

                &--text{
                    font-family: 'Muli-Light', sans-serif;
                    line-height: 25px;
                    font-size: 15px;
                    color: #8e8f88;
                    color: #666;
                }
            }

            &-direita{
                grid-column: 3/-1;
                grid-row: 2/3;

                &--title{
                    @include sub-titulo;
                }

                &--text{
                    font-family: 'Muli-Light', sans-serif;
                    line-height: 25px;
                    font-size: 15px;
                    color: #8e8f88;
                    color: #666;
                }
            }
        }

        
    }
</style>