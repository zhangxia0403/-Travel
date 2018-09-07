<template>
    <div>
        <div class="search">
            <input
                    class="search-input"
                    type="text"
                    placeholder="输入城市名或拼音"
                    v-model="keyword"
            />
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul>
                <li
                        class="search-item border-bottom"
                        v-for="item of list"
                        :key="item.id"
                        @click="handleCityClick(item.name)"
                >
                    {{item.name}}
                </li>
                <li
                        class="search-item border-bottom"
                        v-show="hasNoData"
                >
                    没有找到数据
                </li>
            </ul>
        </div>
    </div>

</template>

<script>

    import BScroll from 'better-scroll'

    export default {
        name: 'CitySearch',
        props: {
            cities: Object
        },
        data(){
            return {
                keyword: '',
                list: [],
                timer: null,
                listShow: false
            }
        },
        watch: {
            keyword () {
                if (this.timer) {
                    clearTimeout(this.timer)
                }
                if (!this.keyword) {
                    this.list = [];
                    return
                }
                this.timer = setTimeout(() => {
                    const result = [];
                    for (let i in this.cities) {
                        this.cities[i].forEach((value) => {
                            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
                                result.push(value)
                            }
                        })
                    }
                    this.list = result
                },100)
            }
        },
        methods:{
            handleCityClick (city) {
                this.$store.commit('changeCity',city);
                this.$router.push('/')
            }
        },
        computed:{
            hasNoData () {
                return !this.list.length
            }
        },
        mounted () {
            this.scroll = new BScroll(this.$refs.search)
        }

    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .search
        height: .72rem
        padding: 0 .1rem
        background: $bgcolor
        .search-input
            width: 100%
            height: .62rem
            line-height: .62rem
            border-radius: .06rem
            padding: 0 .1rem
            text-align: center
            box-sizing: border-box
    .search-content
        overflow: hidden
        position: absolute
        top: 79px
        left: 0
        right: 0
        bottom: 0
        z-index: 1
        background: #eee
        .search-item
            line-height: .62rem
            padding-left: .2rem
            color: #666
            background: #ffffff

</style>
