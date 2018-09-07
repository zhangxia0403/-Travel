<template>
    <div>
        <detail-banner
                :sightName="sightName"
                :bannerImg="bannerImg"
                :bannerImgs="gallaryImgs"
        ></detail-banner>
        <detail-header></detail-header>
        <detail-list :list="list"></detail-list>
    </div>
</template>

<script>
    import DetailBanner from "./components/Banner";
    import DetailHeader from "./components/Header";
    import DetailList from "./components/List";
    import axios from 'axios'

    export default {
        name: 'Detail',
        components: {
            DetailList,
            DetailHeader,
            DetailBanner
        },
        data(){
            return {
                sightName: '',
                bannerImg: '',
                gallaryImgs: [],
                list: []
            }
        },
        mounted(){
            this.getDetailInfo()
        },
        methods: {
            getDetailInfo () {
                axios.get('/api/detail.json',{
                    params: {
                        id: this.$route.params.id
                    }
                }).then(this.handleGetDetail)
            },
            handleGetDetail (res) {
                if (res.data.ret && res.data.data){
                    const data = res.data.data;
                    this.sightName = data.sightName;
                    this.bannerImg = data.bannerImg;
                    this.gallaryImgs = data.gallaryImgs;
                    this.list = data.categoryList
                }
            }
        }

    }
</script>

<style lang="stylus" scoped>

</style>
