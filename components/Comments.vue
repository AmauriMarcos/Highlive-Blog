<template>
  <div class="comments">
      <h2 class="commments__title"></h2>
      <Disqus class="comments__disqus"></Disqus>
  </div>
</template>

<script>
export default {
  props: ['id']
}
</script>

<style lang="scss">
    .comments{
        width: 100%;

         &__title{
              @include sub-titulo;    
            }

        &__disqus{
            width: 100%;
  
             &::before{
                content: "";
                background-color: #323232;
                height: 1px;
                width: 100%;
                z-index: 800;
                display: inline-block;
                text-align: center;
            
            }
        }
    }
</style>