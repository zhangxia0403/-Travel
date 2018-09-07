<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img :src="bannerImg" alt="" class="banner-img">
            <div class="banner-info">
                <div class="banner-title">{{sightName}}</div>
                <div class="banner-number">{{this.bannerImgs.length}}</div>
            </div>
        </div>
        <common-fade>
            <common-gallary
                    :imgs="bannerImgs"
                    v-show="showGallary"
                    @close="handleBannerClose"
            ></common-gallary>
        </common-fade>
    </div>
</template>

<script>
    import CommonGallary from 'common/gallary/Gallary'
    import CommonFade from "common/fade/Fade";

    export default {
        name: 'DetailBanner',
        props:{
            sightName: String,
            bannerImg: String,
            bannerImgs: Array
        },
        components: {
            CommonFade,
            CommonGallary
        },
        data(){
            return {
                showGallary: false
            }
        },
        mounted(){

        },
        methods: {
            handleBannerClick () {
                this.showGallary = true
            },
            handleBannerClose () {
                this.showGallary = false
            }
        }

    }
</script>

<style lang="stylus" scoped>
    .banner
        overflow: hidden
        height: 0;
        padding-bottom: 55%
        position: relative
        .banner-img
            width: 100%
        .banner-info
            display: flex
            position: absolute
            left: 0
            right: 0
            bottom: 0
            line-height: .6rem
            color: #fff
            background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
            .banner-title
                flex: 1
                font-size: .23rem
                text-indent: .2rem
            .banner-number
                background: rgba(0,0,0,.3)
                padding: 0 .4rem
                font-size: .23rem
                height: .32rem
                line-height: .32rem
                border-radius: .2rem
                margin-top: .13rem
</style>
