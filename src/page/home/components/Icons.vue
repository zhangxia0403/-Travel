<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) in pages" :key="index">
                <div class="icon" v-for="item in page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-imgurl" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>

    </div>
</template>

<script>
    export default {

        name: 'HomeIcon',

        data(){
            return {
                swiperOption:{
                    autoplay: false
                },
            }
        },
        props:{
            icon:Array
        },
        computed:{
            pages (){
                // 普通数组转化为二维数组
                const pages = [];
                this.icon.forEach((item,index)=>{
                    const page = Math.floor(index/8);
                    if (!pages[page]){
                        pages[page] = []
                    }
                    pages[page].push(item)
                });
                return pages
            }
        },
        mounted(){

        },
        methods: {}

    }
</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl'
    .icons >>> .swiper-container
        height: 0
        padding-bottom: 50%
    .icons
        margin-top: .1rem
        .icon
            position: relative
            overflow: hidden
            float: left;
            width: 25%
            height: 0;
            padding-bottom: 25%
            text-align: center
            .icon-img
                position: absolute
                top: 0
                left: 0
                right: 0
                bottom: .44rem
                box-sizing: border-box
                padding: .1rem 0
                .icon-imgurl
                    height: 100%
            .icon-desc
                position: absolute
                left: 0
                right: 0
                bottom: 0
                height: .44rem
                line-height: .44rem
                ellipse()
</style>
