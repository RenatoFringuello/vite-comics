<script>
    export default {
        props : {
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
    <div @mouseenter="isHover = true" @mouseleave="isHover = false" class="card">
        <div class="img-container">
            <img :src="thumb" :alt="series">
        </div>
        <div class="text">{{ series.toUpperCase() }}</div>
        <div class="text" :class="isHover ? 'visible' : 'hidden' ">{{ price }}</div>
    </div>
</template>

<style lang="scss" scoped>
    div.card{
        width: calc((100% / 6) - 1.4rem);
        margin :1rem .7rem 0rem;
        
        .img-container img{
            width: 100%;
            height: 178px;
            object-fit: cover;
            object-position:top;
        }
        .text{
            font-size: .7rem;
            color:white;
            margin: .5rem 0;
            &.visible{
                visibility: visible;
            }   
            &.hidden{
                visibility: hidden;
            }   
        }
    }
</style>