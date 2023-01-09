<script>
    export default {
        
    }
</script>

<template>
    <section>
        <div class="container">
            <div class="sign-up">
                <button>sign up now</button>
            </div>
            <nav class="social">
                <h1 class="sans-narrow">follow us</h1>
                <ul>
                    <li><a href="#"><img src="../assets/img/footer-facebook.png" alt="Facebook logo"></a></li>
                    <li><a href="#"><img src="../assets/img/footer-facebook.png" alt="Facebook logo"></a></li>
                    <li><a href="#"><img src="../assets/img/footer-facebook.png" alt="Facebook logo"></a></li>
                    <li><a href="#"><img src="../assets/img/footer-facebook.png" alt="Facebook logo"></a></li>
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
        padding: 1.5rem 0;

        button{
            padding:1.5rem 2rem;
            border:2px solid $main-dc-color;
            color: white;
            background-color: #0000;
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
            }
        }
    }
</style>