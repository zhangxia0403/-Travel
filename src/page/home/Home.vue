<template>
    <div>
        <home-header></home-header>
        <home-swiper :list="swiperList"></home-swiper>
        <home-icon :icon="iconList"></home-icon>
        <home-recommend :list="recommendList"></home-recommend>
        <home-weekend :list="weendList"></home-weekend>
    </div>
</template>

<script>
    import HomeHeader from './components/Header.vue'
    import HomeSwiper from './components/Swiper.vue'
    import HomeIcon from './components/Icons.vue'
    import HomeRecommend from './components/Recommend.vue'
    import HomeWeekend from './components/Weekend.vue'
    import axios from 'axios'
    import { mapState } from 'vuex'

    export default {
        name: 'Home',
        components:{
            HomeHeader,
            HomeSwiper,
            HomeIcon,
            HomeRecommend,
            HomeWeekend
        },
        data(){
            return {
                lastCity:'',
                swiperList: [],
                iconList: [],
                recommendList: [],
                weendList: []
            }
        },
        computed: mapState([
            "city"
        ]),
        methods: {
            getHomeInfo (){
                axios.get('/api/index.json?city=' + this.city)
                    .then(this.getHomeInfoSucc)
            },
            getHomeInfoSucc (res){
                if(res.data.ret && res.data.data){
                    const data = res.data.data;
                    this.swiperList = data.swiperList;
                    this.iconList = data.iconList;
                    this.recommendList = data.recommendList;
                    this.weendList = data.weekendList;
                }
            }
        },
        mounted () {
            this.lastCity = this.city;
            this.getHomeInfo()
        },
        activated () {
            if (this.lastCity !== this.city) {
                this.lastCity = this.city;
                this.getHomeInfo()
            }
        }

    }
</script>

<style scoped>

</style>
