<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
            <swiper :options="swiperOption">
                <swiper-slide v-for="(item,index) of imgs" :key="index">
                    <img class="gallary-img" :src="item" alt="">
                </swiper-slide>
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CommonGallary',
        props: {
            imgs:{
                type: Array,
                default () {
                    return ['http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_600x330_f922b488.jpg']
                }
            }
        },
        data(){
            return {
                swiperOption:{
                    pagination: '.swiper-pagination',
                    paginationType: 'fraction',
                    observeParents: true,  // 只要dom元素发上变化，自我刷新一次
                    observer: true
                },
            }
        },
        methods: {
            handleGallaryClick () {
                this.$emit('close')
            }
        }

    }
</script>

<style lang="stylus" scoped>
    .container >>> .swiper-container
        overflow: inherit
    .container
        display: flex
        flex-direction: column
        justify-content center
        position: fixed
        top: 0
        left: 0
        right: 0
        bottom: 0
        background: #000
        z-index: 99
        .wrapper
            height: 0
            width: 100%
            padding-bottom: 100%
            .gallary-img
                width: 100%
            .swiper-pagination
                color: #fff
                bottom: -1rem
</style>
