<template>
    <div class="header">
       <div class="header-left"><</div>
        <div class="header-input">输入城市/景点/游玩主题</div>
        <div class="header-right">城市</div>
    </div>
</template>

<script>

    export default {
        name: 'HomeHeader',
        data(){
            return {

            }
        },
        mounted(){

        },
        methods: {}

    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .header
        display: flex
        height: .86rem
        line-height: .86rem
        background: $bgcolor
        color: #fff
        .header-left
            width: .64rem
            float: left
            font-size: .5rem
            text-align: center
        .header-input
            flex: 1
            background: #ffffff
            border-radius: .1rem
            margin-top: .12rem
            height: .64rem
            margin-left: .2rem
            color: #ccc
            line-height: .64rem
            text-indent: .1rem
        .header-right
            width: 1.24rem
            float: right;
            text-align: center

</style>
