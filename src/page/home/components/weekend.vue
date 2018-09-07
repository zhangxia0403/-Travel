<template>
    <div>
        <div class="recommend-title">周末游</div>
        <ul class="item-box">
            <li class="item" v-for="item in list" :key="item.id">
                <img class="item-img" :src="item.imgUrl" alt="">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'HomeWeekend',
        data(){
            return {

            }
        },
        props:{
            list:Array
        }

    }
</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl'
    .recommend-title
        line-height: .8rem
        text-indent: .4rem
        background: #eee
    .item-box
        background: #eee
        .item
            overflow: hidden
            padding-bottom: .1rem
            .item-img
                width: 100%
            .item-info
                padding: .1rem
                min-width: 0
                background: #fff
                .item-title
                    line-height: .54rem
                    font-size: .32rem
                .item-desc
                    line-height: .4rem
                    color: #999
                    ellipse()



</style>

