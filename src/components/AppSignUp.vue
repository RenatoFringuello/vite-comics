<script>
    export default {
        data(){
            return{
                socialImgs:[
                    {title:'Ffacebook logo',src:'../assets/img/footer-facebook.png'},
                    {title:'Twitter logo',src:'../assets/img/footer-twitter.png'},
                    {title:'YouTube logo',src:'../assets/img/footer-youtube.png'},
                    {title:'Pinerest logo',src:'../assets/img/footer-pinterest.png'},
                    {title:'Periscope logo',src:'../assets/img/footer-periscope.png'},
                ]
            }
        },
        methods: {
            getImgPath(path){
                return new URL(path, import.meta.url).href;
            }
        },
    }
</script>

<template>
    <section>
        <div class="container">
            <div class="sign-up">
                <button>sign-up now!</button>
            </div>
            <nav class="social">
                <h1 class="sans-narrow">follow us</h1>
                <ul>
                    <li v-for="img in socialImgs" ><a href="#"><img :src="getImgPath(img.src)" :alt="img.title"></a></li>
                </ul>
            </nav>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;
    section{
        background-color: $sign-up-bg;
    }
    .container{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.8rem 0;

        button{
            text-transform: uppercase;
            font-weight: 600;
            padding:.8rem;
            border:2px solid $main-dc-color;
            color: white;
            background-color: #0000;
            cursor: pointer;

            &:hover{
                background: $btn-hover;
            }
        }
        nav.social{
            display: flex;
            align-items: center;

            h1{
                text-transform: uppercase;
                color: $main-dc-color ;
            }
            ul{
                margin-left: 1rem;
                display: flex;
                li{
                    margin-left: 1rem;
                    
                    a:hover{
                        opacity:.7;
                    }
                }
            }
        }
    }
</style>