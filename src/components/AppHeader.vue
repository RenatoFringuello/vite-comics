<script>
    export default {
        data(){
            return{
                isActive:0,
                links : [
                    {title:'characters'},
                    {title:'comics'},
                    {title:'movies'},
                    {title:'tv'},
                    {title:'games'},
                    {title:'collectibles'},
                    {title:'videos'},
                    {title:'fans'},
                    {title:'news'},
                    {title:'shop'},
                ]
            }
        }    
    }
</script>

<template>
   <header class="sans-narrow">
    <div class="container">
        <div class="img-container">
            <img src="../assets/img/dc-logo.png" alt="DC Logo">
        </div>
        <nav class="nav-links">
            <ul>
                <li v-for="link, i in links" @click="isActive = i"  :class="isActive === i ? 'active' : ''">
                    <a href="#">{{link.title.toUpperCase()}}</a>
                    <div class="active-bar"></div>
                </li>
            </ul>
        </nav>
    </div>
   </header>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;

    header {
        background-color: white;
        div.container{
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;

            .img-container > img{
                height: 70px;
            }

            nav.nav-links ul li{
                margin: 0 1rem;
                padding: 45px 0;
                position: relative;
                text-align: center;
                cursor: pointer;

                &.active .active-bar,
                &:hover .active-bar{
                    display: block;
                }
                &.active a{
                    color: $main-dc-color;;
                }

                a{
                    font-size: .8rem;
                    color: $main-text-color;
                    font-weight: bold;
                }
                .active-bar{
                    display: none;

                    position: absolute;
                    bottom: 0;
                    width: 100%;
                    height: .25rem;
                    background-color: $main-dc-color;
                }
            }
        }
    }
</style>