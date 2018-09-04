<template>

    <div class="wrapper">
        <swiper :options="swiperOption">
            <swiper-slide v-for="item of swiperList" :key="item.id">
                <img class="swiper-img" :src="item.imgurl" alt="">
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
                swiperList:[
                    {
                        id: '001',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1808/70/5603e6a535062402.jpg_750x200_2c552f2c.jpg'
                    },
                    {
                        id: '002',
                        imgurl: 'https://img1.qunarzz.com/piao/fusion/1808/fd/fddc5309111a0402.jpg_750x200_e7b93551.jpg'
                    }
                ]
            }
        },
        computed:{

        },
        mounted(){

        },
        methods: {}

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
        padding-bottom: 26.67%
        background: #f2f2f2
        .swiper-img
            width: 100%

</style>
