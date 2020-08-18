<template>
   <section class="cover">
     <div class="cover__main-box">
        <h1>SOME CONTENT</h1>
        <h3>Chamada</h3>
     </div>
     <div class="cover__box-up">
       <h1>SOME CONTENT</h1>
        <h3>Chamada</h3>
     </div>
     <div class="cover__box-down">
       <h1>SOME CONTENT</h1>
        <h3>Chamada</h3>
     </div>
   </section>
</template>

<script>
export default {

}
</script>
<style lang="scss">
  .cover{
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 5px;
    padding: 0 5%;

    &__main-box{
      grid-column: 1/5;
      grid-row: 1/3;
      background-color: brown;
      width: 100%;
      height: 65vh;
     
    }

    &__box-up{
      grid-column: 5/-1;
      grid-row: 1/2;
      background-color: rgb(118, 177, 162);
      width: 100%;
    }

    &__box-down{
      grid-column: 5/-1;
      grid-row: 2/3;
      background-color: rgb(80, 71, 209);
      width: 100%;

    }
  }

</style>