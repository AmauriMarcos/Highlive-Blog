<template>
    <div class="newsletter">
        <h2 class="title-newsletter">Assine nossa newsletter</h2>
        <form @submit.prevent='submitNewsletter' class="form">
            <input type="text" placeholder="Nome" v-model="form.nome" class="form__input">
            <input type="text" placeholder="Sobrenome" v-model="form.sobrenome" class="form__input">
            <input type="email" placeholder="Email" v-model="email" class="form__input">
            <button type="submit" class="form__button">Enviar</button>
        </form>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            form: [
                {nome: '', sobrenome: ''}
            ],
            email: ''
        }
    },
    methods:{
        submitNewsletter(){
            axios.post("https://highlive.netlify.app/.netlify/functions/index",  { email: this.email },
                { headers : {
                    "Content-Type": "application/json"
                }}
            ).then((res) =>{
                console.log(res.status)
            }).catch(error => {console.log(error)})

            /* this.$toasted.success("Thank you for your subscription !!!", { 
                theme: "toasted-primary", 
                position: "top-left", 
                containerClass: 'myContainer',
                fitToScreen: true,
                fullWidth: true,
                duration : 5000
            })  */

            this.form.nome = ''
            this.form.sobrenome = ''
            this.email = ''
        
        } 
    }
}
</script>

<style lang="scss">
    .newsletter{
        padding: 5% 0;
    }
    .title-newsletter{
        @include sub-titulo;
        font-size: 1.9rem;
        font-weight: 400;
        
    }
    .form{
        @include center;
        

        &__input{
            width: 221px;
            height: 46px;
            padding: 12px 20px;
            font-size: 13px;
            font-family: 'Open Sans', sans-serif;
            text-align: left;
            letter-spacing: .9px;
            border:none;
            border: 1px solid #ddd;
            margin-right: .5rem;
           /*  text-transform: uppercase; */
        }

        &__button{
             font-family: 'Open Sans', sans-serif;
            background-color: $black;
            padding: 12px 20px;;
            font-size: 14px;
            text-align: center;
            color: $white;
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: .9px;
        }
    }


</style>