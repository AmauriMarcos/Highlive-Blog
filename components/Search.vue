<template>
    <div class="search">
        <form @submit.prevent='submitSearch()' class="search__form">
            <input class="search__input" type="text" placeholder="Pesquisar...">
        </form>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    .search{

        &__form{
            display: flex;
            justify-content: center;
            margin: 1rem 0;
        }

        &__input{
            border: none;
            border: 1px solid rgb(0, 0, 0);
            padding: .7rem .4rem;
            outline: none;
        }
    }
</style>