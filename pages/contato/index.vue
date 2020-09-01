<template>
    <div class="contato">
        <h2 class="contato__title">Tá querendo conversar, é?</h2>
        <form   @submit.prevent='submitForm' 
                action="/" 
                class="contato__form"
                data-netlify="true"
                netlify-honeypot="bot-field" 
                method="post"  
                name="highlive"
        >

            <input type="hidden" name="form-name" value="highlive" />

            <label class="contato__form-label" for="name">Nome</label>
            <input class="contato__form-input" type="text" id="name" name="name" v-model="form.name">

            <label class="contato__form-label" for="email">Email</label>
            <input class="contato__form-input" type="email" id="email" name="email" v-model="form.email">

            <label class="contato__form-label" for="subject">Assunto</label>
            <input class="contato__form-input" type="text" id="subject" name="subject" v-model="form.subject">

            <label class="contato__form-label" for="message">Mensagem</label>
            <textarea class="contato__form-message" name="message" id="message" v-model="form.message"></textarea>

            <button type="submit" class="contato__form-btn">Enviar</button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            form:  {
                name: '',
                email: '',
                subject: '',
                message: ''
            }
            
        }
    },
    methods:{
        encode(data){
            return Object.keys(data)
            .map(key => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`)
            .join('&')
        },

        submitForm(){
     
            fetch('/', {
                method: 'post',
                headers: {
                    'Content-type': 'application/x-www-form-urlencoded'
                },
                body: this.encode({
                    'form-name': 'highlive',
                    ...this.form
                })              
            })
            .then(() =>{
                this.$router.push({ path: '/' });
                window.scrollTo(0,0);
                this.form.name= '';
                this.form.subject= '';
                this.form.email= '';
                this.form.message = '';  
              /*   this.$toasted.success("Message sent successfully", { 
                    theme: "toasted-primary", 
                    position: "top-left", 
                    containerClass: 'myContainer',
                    fitToScreen: true,
                    fullWidth: true,
                    duration : 5000
                });  */                       
            })
            .catch((err) => console.log(`Error: ${err}`));
            
        }
    }
}
</script>

<style lang="scss">
    .contato{
        height: 75vh;
        @include center;
        flex-direction: column;

        &__title{
            @include sub-titulo;
            font-size: 2rem;
        }

        &__form{
            @include center;
            flex-direction: column;
            margin-top: .7rem;

            &-label{
                font-size: .7rem;
                transform: translate(-7.5rem);
                font-family: 'Open Sans', sans-serif;
                font-size: 300;
            }

            &-input{
                border: none;
                border: 1px solid rgb(0, 0, 0);
                padding: .5rem .4rem;
                outline: none;
                width: 20rem;
                margin-bottom: .5rem;
                border-radius: 3px;
            }

            &-message{
                border: 1px solid black;
                outline: none;
                width: 20rem;
                border-radius: 3px;
                resize: none;
                height: 8rem;
            }

            &-btn{
                background-color: $black;
                font-family: 'Open Sans', sans-serif;
                padding: .7rem 1.2rem;
                color: $white;
                outline: none;
                width: 20rem;
                margin-top: 1rem;
                border-radius: 3px;
                text-transform: uppercase;
                font-weight: 300;
            }
        }
    }
</style>