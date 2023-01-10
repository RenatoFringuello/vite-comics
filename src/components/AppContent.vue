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
        <div class="jumbotron">
            <div class="container">
                <h2 class="sans-narrow filled">current series</h2>
            </div>
        </div>
        <div class="container">
            <div class="wrapper">
                <AppContentBook v-for="book in comicBooks"
                    :thumb="book.thumb"
                    :price="book.price"
                    :series="book.series"
                    :type="book.type"/>
            </div>
            <div class="btn-container">
                <button class="sans-narrow filled">load more</button>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;

    section{
        color:white;

        .jumbotron {
            
            height: 300px;
            background:url('../assets/img/jumbotron.jpg') no-repeat;
            background-size: cover;
            
            .container{
                position: relative;
                height: 100%;
                h2.filled{
                    position: absolute;
                    transform: translateY(50%);
                    bottom:0;
                    padding: .8rem 1.5rem;
                }
            }

        }
        .container{
            padding: 1.5rem 1rem;

            .wrapper{
                display: flex;
                flex-wrap: wrap;
                justify-content: space-between;
                padding: 0 1rem;
            }
            .btn-container{
                text-align: center;
            }
        }
        
        .sans-narrow{
            text-transform: uppercase;
        }
    }
</style>