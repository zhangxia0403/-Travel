<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <div class="header-back"><</div>
        </router-link>
    </div>
</template>

<script>
    export default {

        name: 'CityHeader',

        data(){
            return {

            }
        },

    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .header
        overflow: hidden
        height: $headerHeight
        line-height: $headerHeight
        font-size: .32rem
        text-align: center
        background: $bgcolor
        color: #fff
        position: relative
        .header-back
            position: absolute
            top: 0
            width: .64rem
            color: #fff
            font-size: .4rem

</style>
