<template>

    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <swiper-slide v-for="item of list" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl" alt="">
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>

</template>

<script>
    export default {
        name: 'HomeSwiper',
        data(){
            return {
                swiperOption:{
                    pagination: '.swiper-pagination',
                    loop: true
                },
            }
        },
        props:{
           list: Array
        },
        computed:{
            showSwiper (){
                return this.list.length
            }
        },

    }
</script>

<style lang="stylus" scoped>
    /*样式穿透*/
    .wrapper >>> .swiper-pagination-bullet-active
         background: #fff
    .wrapper
        width: 100%
        /*图片高度相对于宽度的百分比*/
        overflow: hidden
        height: 0
        padding-bottom: 31.25%
        background: #f2f2f2
        .swiper-img
            width: 100%

</style>
