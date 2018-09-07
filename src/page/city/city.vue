<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list
                :cities="cities"
                :hot="hotCities"
                :letter="letter"
        ></city-list>
        <!--父组件通过监听子组件向上传递的事件 接收子组件的数据-->
        <city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
    </div>
</template>

<script>
    import CityHeader from './components/Header'
    import CitySearch from "./components/Search";
    import CityList from "./components/List";
    import CityAlphabet from "./components/Alphabet";
    import axios from 'axios'

    export default {
        name: 'City',
        data(){
            return {
                cities: {},
                hotCities: [],
                letter: ''
            }
        },
        components:{
            CityAlphabet,
            CityList,
            CitySearch,
            CityHeader
        },
        methods:{
            getCityInfo () {
                axios.get('/api/city.json').then(this.getCity)
            },
            getCity (res) {
                if(res.data.ret && res.data.data){
                    const data = res.data.data;
                    this.cities = data.cities;
                    this.hotCities = data.hotCities;
                }
            },
            // 父组件拿到子组件的数据，进行一些其他操作
            handleLetterChange (letter){
                this.letter = letter
            }
        },
        mounted () {
            this.getCityInfo()
        }

    }
</script>

<style scoped>


</style>
