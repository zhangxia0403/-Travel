<template>
    <div>
        <router-link
                tag="div"
                to="/"
                class="header-abs"
                v-show="showAbs"
        ><</router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            景点详情
            <div class="header-fixed-back"><</div>
        </div>
    </div>
</template>

<script>
    export default {

        name: 'DetailHeader',

        data(){
            return {
                showAbs: true,
                opacityStyle: {
                    opacity: 0
                }
            }
        },
        mounted(){

        },
        methods: {
            handleScroll () {
                const top = document.documentElement.scrollTop;
                if( top > 60 ){
                    let opacity = top / 140;
                    opacity = opacity > 1 ? 1 : opacity;
                    this.opacityStyle = {
                        opacity
                    };
                    this.showAbs = false
                } else {
                    this.showAbs = true
                }
            }
        },
        // app 使用了 keep-alive 所以vue 会提供两个生命周期函数 activated  deactivated
        activated () {
            // 给全局 window 添加事件，需要对全局事件解绑
            // 全局下的事件，在每个页面都会触发，所以可能存在页面功能之间相互影响，出现bug
            // 为了避免出现页面之间相互影响，就需要对全局事件进行解绑
            window.addEventListener('scroll',this.handleScroll)
        },
        deactivated () {  // 页面切换的时候
            window.removeEventListener('scroll',this.handleScroll)
        }

    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .header-abs
        position: absolute
        left: .2rem
        top: .2rem
        width: .6rem
        height: .6rem
        line-height: .6rem
        text-align: center
        border-radius: .4rem
        background: rgba(0,0,0,.5)
        color: #fff
    .header-fixed
        height: 0.86rem
        line-height: 0.86rem
        font-size: 0.32rem
        text-align: center
        background: #00bcd4
        color: #fff
        position: fixed
        top: 0
        left: 0
        right: 0
        z-index: 2
        .header-fixed-back
            position: absolute
            top: 0
            left: 0
            width: .64rem
            color: #fff
            font-size: .4rem

</style>
