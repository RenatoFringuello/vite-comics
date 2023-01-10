<script>
    export default {
        props : {
            nBookPerRow: Number,
            thumb: String,
            price: String,
            series: String,
            type: String,
        },
        data() {
            return {
                isHover : false
            }
        },
    }
</script>

<template>
    <div 
        @mouseenter="isHover = true" 
        @mouseleave="isHover = false" 
        class="card"
        :style="`width: calc((100% / ${nBookPerRow}) - 1rem);`"
        >
        <div class="img-container">
            <img :style="`height: calc((1200px / ${nBookPerRow}) - 1rem);`" :src="thumb" :alt="series">
        </div>
        <div class="text">{{ series.toUpperCase() }}</div>
        <div class="text" :class="isHover ? 'visible' : 'hidden' ">{{ price }}</div>
    </div>
</template>

<style lang="scss" scoped>
    @use '../style/partials/variables' as *;
    $margin-bottom:1rem;
    div.card{
        // width: calc((100% / 6) - 1rem);
        padding-top :1rem;
        cursor: pointer;
        
        .img-container {
            margin-bottom: $margin-bottom;
            img{
                width: 100%;
                // height: calc((1200px / 6) - 1rem);
                object-fit: cover;
                object-position:top;
                display: block;
            }
        }
        .text{
            font-size: .7rem;
            color:white;
            &.visible{
                visibility: visible;
            }   
            &.hidden{
                visibility: hidden;
            }   
        }
    }
</style>