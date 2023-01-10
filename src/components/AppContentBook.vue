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
    @use '../style/partials/variables' as *;
    $margin-bottom:1rem;
    div.card{
        width: calc((100% / 6) - 1rem);
        padding-top :1rem;
        cursor: pointer;
        
        .img-container {
            margin-bottom: $margin-bottom;
            img{
                width: 100%;
                height: 178px;
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