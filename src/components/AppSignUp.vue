<script>
    export default {
        data(){
            return{
                superheroes : [
                    {heroname:'alan scott', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_AlanScott_5fb82459209669.21120396.jpg?itok=UNwirSPN'},
                    {heroname:'amethyst', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Amethyst_5c40e299329fa8.64612837.jpg?itok=kSiOE1F5'},
                    {heroname:'antiope', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Antiope_5efcf761a6d6c1.75705997.jpg?itok=KNOANzS6'},
                    {heroname:'aquaman', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Aquaman_5c411a95e70ff5.50429372.jpg?itok=jQSdLKTj'},
                    {heroname:'batman', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Batman_20190116_5c3fc4b40fae42.85141247.jpg?itok=O3UVj2Np'},
                    {heroname:'batwoman', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Batwoman_5c4111746bf769.13954525.jpg?itok=Pg99WDZ8'},
                    {heroname:'black canary', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_BlackCanary_5c41184e20ee69.98463239.jpg?itok=7TPBWxO2'},
                    {heroname:'captain marvel jr.', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_CaptainMarvelJR_5ca81decc796e3.60776207.jpg?itok=EmSB_Lp1'},
                    {heroname:'cyborg', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Cyborg_20190116_5c3fcd9048a0e1.41912254.jpg?itok=USYEPW2a'},
                    {heroname:'doctor fate', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_DoctorFate_6347343a407578.59680601.jpg?itok=2IcyEgi0'},
                    {heroname:'green lantern', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_GreenLantern_20200721_5f173ac65f56f7.70929296.jpg?itok=xBqN4E8b'},
                    {heroname:'shazam', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Shazam_5c53a74aefbb12.02099042.jpg?itok=qhT5pUgT'},
                    {heroname:'superman', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Superman_5c3fc2758f6984.90100206.jpg?itok=esABWATU'},
                    {heroname:'supergirl', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Supergirl_5b6b48c92a5d42.10749263.jpg?itok=cL4AzPZY'},
                    {heroname:'the flash', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_Flash_20190116_5c3fcaaa18f023.90325986.jpg?itok=_5BRdVMO'},
                    {heroname:'wonder woman', imgSrc:'https://www.dc.com/sites/default/files/styles/comics320x485/public/Char_Thumb_WonderWoman_20190116_5c3fc6aa51d064.76155401.jpg?itok=xyMebvMu'},
                ],
                userSigned:[],
                socialImgs:[
                    {title:'Ffacebook logo',imgName:'footer-facebook.png'},
                    {title:'Twitter logo',imgName:'footer-twitter.png'},
                    {title:'YouTube logo',imgName:'footer-youtube.png'},
                    {title:'Pinerest logo',imgName:'footer-pinterest.png'},
                    {title:'Periscope logo',imgName:'footer-periscope.png'},
                ],
                showSignUp :false,
                userName:'',
                userLastName:'',
                userEmail:'',
                userBirthDate:'',
                userFavHero:'alan scott',
                userHeroIndex : 0
            }
        },
        methods: {
            getImgPath(imgName){
                return new URL(`../assets/img/${imgName}`, import.meta.url).href;
            },
            closeForm(){
                this.showSignUp = false;
                this.userName = '';
                this.userLastName = '';
                this.userEmail = '';
                this.userBirthDate = '';
                this.userFavHero = this.superheroes[0].heroname;
                this.userHeroIndex = 0;
            },
            saveData(){
                if( this.userName.trim() !== '' &&
                    this.userLastName.trim() !== '' &&
                    this.userEmail.trim() !== '' &&
                    this.userBirthDate.trim() !== ''){
                    
                    this.userSigned.push({
                        firstName : this.userName.trim(),
                        lastName :  this.userLastName.trim(),
                        email :     this.userEmail.trim(),
                        birthDate : this.userBirthDate.trim(),
                        favHero :   this.userFavHero,
                    });
                    this.closeForm();
                }
            },
            getHeroCapitalized(hero){
                const heroSpittedNames = hero.split(' ');
                let heroname = '';
                heroSpittedNames.forEach((name)=>{
                    heroname += `${name.charAt(0).toUpperCase() + name.slice(1, name.length)} `;
                });
                return heroname;
            },
        }
    }
</script>

<template>
    <section>
        <div class="container">
            <div class="sign-up">
                <button class="outlined" @click="showSignUp = true">sign-up now!</button>
            </div>
            <nav class="social">
                <h1 class="sans-narrow">follow us</h1>
                <ul>
                    <li v-for="img in socialImgs" ><a href="#"><img :src="getImgPath(img.imgName)" :alt="img.title"></a></li>
                </ul>
            </nav>
            <div class="wrapper" :class="showSignUp ? 'd-flex' : 'd-none'">
                <form>
                    <label for="name"><h1 class="sans-narrow">Name</h1></label>
                    <input type="text" id="name" placeholder="type your name..." required v-model="userName">
                    <label for="last-name"><h1 class="sans-narrow">Last Name</h1></label>
                    <input type="text" id="last-name" placeholder="type your last name..." required v-model="userLastName">
                    <label for="email"><h1 class="sans-narrow">E-mail</h1></label>
                    <input type="email" id="email" placeholder="type your e-mail..." required v-model="userEmail">
                    <label for="birth-date"><h1 class="sans-narrow">Birth Date</h1></label>
                    <input type="date" id="birth-date" required v-model="userBirthDate">
                    <label for="fav-hero"><h1 class="sans-narrow">Favourite Superhero</h1></label>
                    <div class="select-box">
                        <div class="img-container">
                            <img :src="superheroes[userHeroIndex].imgSrc" :alt="superheroes[userHeroIndex].heroname">
                        </div>
                        <select id="fav-hero" v-model="userFavHero">
                            <option 
                                @click="userHeroIndex = i"
                                @keyup.Enter="userHeroIndex = i" 
                                v-for="hero,i in superheroes" 
                                :value="hero.heroname">{{ getHeroCapitalized(hero.heroname) }}</option>
                        </select>
                    </div>
                    <button class="sans-narrow filled" @click="saveData()">Send</button>
                    <button class="sans-narrow filled cross" @click="closeForm()">&Cross;</button>
                </form>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;
    section{
        background-color: $sign-up-bg;
        .container{
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.8rem 1rem;
            
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

            .wrapper{
                position: fixed;
                top: 0;
                left: 0;
                width: 100vw;
                height: 100vh;
                background-color: #0008;

                &.d-flex{
                    display: flex;
                }

                form{
                    position: relative;
                    background-color: white;
                    margin: auto;
                    padding: 2rem;
                    *{
                        display: block;
                    }
                    label{
                        font-size: 1.5rem;
                        color:$main-dc-color;
                    }
                    input,
                    select{
                        width: 400px;
                        background-color: #e3e3e3;
                        padding:.97rem .8rem;
                        margin-bottom:1rem;
                        font-size: 1rem;
                    }
                    .select-box{
                        display: flex;
                        
                        .img-container img{
                            width: 50px;
                            height: 50px;
                            object-fit: cover;
                            object-position:top;
                        }
                        select{
                            width: 100%;
                        }
                    }

                    button{
                        width: 100%;

                        &.cross{
                            position: absolute;
                            top: 1rem;
                            right: 1rem;
                            font-size: 2rem;
                            width: auto;
                            padding: .3rem .5rem .7rem;
                        }
                    }
                }
            }
        }
    }
</style>