<template>
    <div class="footer">
        <p>Copyright @ Highlive Blog</p>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss">
    .footer{
        height: 7rem;
        width: 100%;
        @include center;
        background-color: rgb(27, 27, 27);

        @include respond(phone){
            height: 7rem;
        }

        & p{
           
            color: white;
            font-family: 'Muli-Light', sans-serif;
        }
    }
</style>