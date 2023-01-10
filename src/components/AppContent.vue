<script>
    import dataRaw from '../dc-comics.json';
    import AppContentBook from './AppContentBook.vue';

    export default{
        data() {
            return {
                comicBooks : dataRaw,
            }
        },
        components :{
            AppContentBook,
        }
   }
</script>

<template>
    <section>
        <div class="container">
            <h1 class="sans-narrow">Books</h1>
            <div class="wrapper">
                <AppContentBook v-for="book in comicBooks"
                :thumb="book.thumb"
                :price="book.price"
                :series="book.series"
                :type="book.type"/>
            </div>
            <button class="sans-narrow">load more</button>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;

    section{
        color:white;
        .container{
            padding: 2.5rem 1rem;

            .wrapper{
                display: flex;
                flex-wrap: wrap;
            }
            .sans-narrow{
                text-transform: uppercase;
            }
        }
    }
</style>