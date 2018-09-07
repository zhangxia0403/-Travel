<template>
    <div class="header">
       <div class="header-left"><</div>
        <div class="header-input">输入城市/景点/游玩主题</div>
        <router-link to="/city">
            <div class="header-right">{{this.city}}</div>
        </router-link>

    </div>
</template>

<script>
    import { mapState } from 'vuex'
    export default {
        name: 'HomeHeader',
        computed: mapState([
            "city"
        ])
    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .header
        display: flex
        height: $headerHeight
        line-height: $headerHeight
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
            min-width: 1.04rem
            padding: 0 .2rem
            float: right;
            color: #fff
            text-align: center

</style>
