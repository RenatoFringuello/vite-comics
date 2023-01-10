<script>
    import dataRaw from '../dc-comics.json';
    import AppContentBook from './AppContentBook.vue';

    export default{
        data() {
            return {
                comicBooks : dataRaw,
                nBookPerRow : 6,
                maxBookRequested : 12,
            }
        },
        methods: {
            updateBookShow(n){
                this.nBookPerRow = n;
                if(n % 3 === 0){
                    this.maxBookRequested -= this.maxBookRequested % n;
                }
                else{
                    this.maxBookRequested += this.maxBookRequested % n;
                }
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
            <div class="sort-selection-group">
                <button class="sort-selection-item" @click="updateBookShow(3)">
                    <h3>3</h3>
                </button>
                <button class="sort-selection-item" @click="updateBookShow(4)">
                    <h3>4</h3>
                </button>
                <button class="sort-selection-item" @click="updateBookShow(6)">
                    <h3>6</h3>
                </button>
            </div>
            <div class="wrapper">
                <AppContentBook 
                    v-for="(book, i) in comicBooks"
                    v-show="i < maxBookRequested"
                    :nBookPerRow="nBookPerRow"
                    :thumb="book.thumb"
                    :price="book.price"
                    :series="book.series"
                    :type="book.type"/>
            </div>
            <div class="btn-container">
                <button 
                    class="sans-narrow filled" 
                    :class="comicBooks.length <= maxBookRequested ? 'disabled' :'clickable' " 
                    @click="maxBookRequested += (nBookPerRow * 2)">

                    load more
                </button>
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

            .sort-selection-group{
                display: flex;
                justify-content: flex-end;

                .sort-selection-item{
                    width:  40px;
                    height: 40px;
                    background-color: #0000;
                    color: #fff4;
                    border:2px solid ;
                    margin: 0 .25rem;
                    display: flex;
                    &:hover{
                        color: white;
                    }

                    h3{
                        margin: auto;
                    }
                }
            }
            .wrapper{
                display: flex;
                flex-wrap: wrap;
                justify-content: space-between;
                padding: 0 1rem;
            }
            .btn-container{
                text-align: center;
                padding-top: 1rem;
            }
        }
        
        .sans-narrow{
            text-transform: uppercase;
        }
    }
</style>