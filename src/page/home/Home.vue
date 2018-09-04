<template>
    <div>
        <Home-header></Home-header>
        <Home-swiper></Home-swiper>
        <Home-icon></Home-icon>
    </div>
</template>

<script>
    import HomeHeader from './components/Header.vue'
    import HomeSwiper from './components/Swiper.vue'
    import HomeIcon from './components/Icons.vue'

    export default {
        name: 'Home',
        components:{
            HomeHeader,
            HomeSwiper,
            HomeIcon
        },
        data(){
            return {

            }
        },
        mounted(){

        },
        methods: {}

    }
</script>

<style scoped>

</style>
