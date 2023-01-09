<script>
    export default {
        data(){
            return{
                linksGroups:[
                    {contents:[
                        {title:'dc comics', isTitle: true},
                        {title:'Characters', isTitle: false},
                        {title:'Comics', isTitle: false},
                        {title:'Movies', isTitle: false},
                        {title:'TV', isTitle: false},
                        {title:'Games', isTitle: false},
                        {title:'Videos', isTitle: false},
                        {title:'News', isTitle: false},
                        {title:'SHOP', isTitle: true},
                        {title:'Characters', isTitle: false},
                        {title:'Comics', isTitle: false},
                    ]},
                    {contents:[
                        {title:'dc', isTitle: true},
                        {title:'Term Of Use', isTitle: false},
                        {title:'Privacy policy (New)', isTitle: false},
                        {title:'Ad Choices', isTitle: false},
                        {title:'Advertising', isTitle: false},
                        {title:'Jobs', isTitle: false},
                        {title:'Subscriptions', isTitle: false},
                        {title:'Talent Workshops', isTitle: false},
                        {title:'CPSC Certificates', isTitle: false},
                        {title:'Ratings', isTitle: false},
                        {title:'Shop Help', isTitle: false},
                        {title:'Contact Us', isTitle: false},
                    ]},
                    {contents:[
                        {title:'sites', isTitle: true},
                        {title:'DC', isTitle: false},
                        {title:'MAD Magazine', isTitle: false},
                        {title:'DC Kids', isTitle: false},
                        {title:'DC Universe', isTitle: false},
                        {title:'DC Power Visa', isTitle: false},
                    ]},
                ]
            }
        }    
    }
</script>

<template>
    <section>
        <div class="container">
            <nav>
                <ul v-for="group in linksGroups">
                    <li v-for="content in group.contents"><a href="#" :class="content.isTitle ? 'sans-narrow' : ''">{{ content.title }}</a></li>
                </ul>
            </nav>
            <div class="img-container"></div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;

    section{
        
        background: url('../assets/img/footer-bg.jpg') no-repeat;
        background-size: cover;
        
        .container{
            display: flex;
            justify-content: space-between;
            align-items: center;
            overflow-y: hidden;

            nav{
                display: flex;
                
                ul{
                    margin-right:1.5rem;
                    
                    li{
                        line-height: 1rem;
                        
                        a{
                            font-size: 0.7rem;
                            color:$main-text-color ;
                            
                            &.sans-narrow{
                                text-transform: uppercase;
                                font-size: 1.2rem !important;
                                font-weight: bold;
                                color:#fff;
                                cursor: text;
                                display: block;
                                margin: 1rem 0 .8rem;
                            }
                        }
                    }
                }
            }
            div.img-container{
                background: url('../assets/img/dc-logo-bg.png') no-repeat;
                background-size: cover;
                background-position: center;
                width: 45%;
                height: 330px;
            }
        }
    }
</style>