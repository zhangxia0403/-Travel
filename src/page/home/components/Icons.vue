<template>
    <div class="icons">
        <swiper>
            <swiper-slide v-for="(page,index) of pages">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-imgurl" :src="item.imgurl" alt="">
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
                iconList:[
                    {
                        id: '0001',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0002',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0003',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0004',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0005',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0006',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0007',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0008',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1808/8d/747c9a29b8dba402.png',
                        desc: '热门景点'
                    },
                    {
                        id: '0009',
                        imgurl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
                        desc: '热门景点'
                    },
                ]
            }
        },
        computed:{
            pages (){
                // 普通数组转化为二维数组
                const pages = [];
                this.iconList.forEach((item,index)=>{
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
