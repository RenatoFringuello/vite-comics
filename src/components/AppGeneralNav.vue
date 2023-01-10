<script>
    export default {
        data(){
            return{
                links :[
                    {title:'digital comics', imgName:'buy-comics-digital-comics.png'},
                    {title:'dc merchandise', imgName:'buy-comics-merchandise.png'},
                    {title:'subscription', imgName:'buy-comics-subscriptions.png'},
                    {title:'comic shop locator', imgName:'buy-comics-shop-locator.png'},
                    {title:'dc power visa', imgName:'buy-dc-power-visa.svg'}
                ]
            }
        },
        methods: {
            getImgPath(imgName){
                return new URL(`../assets/img/${imgName}`, import.meta.url).href;
            }
        },
    }
</script>

<template>
    <section>
        <div class="container">
            <nav class="nav-links">
                <ul>
                    <li v-for="link in links" >
                        <img :src="getImgPath(link.imgName)" :alt="link.title">
                        <span>{{link.title.toUpperCase()}}</span>
                    </li>
                </ul>
            </nav>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;

    section{
        background: $main-dc-color;
        color: white;

        .container{
            padding:3rem 2rem;

            .nav-links ul{
                display: flex;
                justify-content: space-between;
             
                li{
                    cursor: pointer;
                    
                    img{
                        height: 50px;
                        max-width: 50px;
                        vertical-align: middle;
                        margin-right: 1rem;
                    }
                    span{
                        font-weight: 300;
                        font-size: .85rem;
                    }
                }
            }
        }
    }

</style>