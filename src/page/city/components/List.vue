<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.$store.state.city}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div
                            class="button-wrapper"
                            v-for="item of hot"
                            :key="item.id"
                            @click="handleCityClick(item.name)"
                    >
                        <div class="button">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area"
                 v-for="(item,key) of cities"
                 :key="key"
                 :ref="key"
            >
                <!--cities 是一个Object 循环用key-->
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div
                            class="item border-bottom"
                            v-for="innerItem of item"
                            :key="innerItem.id"
                            @click="handleCityClick(innerItem.name)"
                    >
                        {{innerItem.name}}
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>

    import BScroll from 'better-scroll'

    export default {
        name: 'CityList',
        props:{
            cities: Object,
            hot: Array,
            letter: String
        },
        methods:{
            handleCityClick (city) {
//                简单的数据不需要调用 dispatch 方法，可直接用 commit
//                this.$store.dispatch('changeCity',city)
                this.$store.commit('changeCity',city);
                this.$router.push('/')
            }
        },
        mounted(){
            const wrapper = this.$refs.wrapper;
            this.scroll = new BScroll(wrapper)
        },
        watch: {  // 监听器
            letter () {  // 监听父组件传来的letter数据，发生变化执行函数
                if(this.letter){
                    const element = this.$refs[this.letter][0];
                    // better-scroll提供的方法
                    // element 必须是一个Dom 元素或 Dom选择器
                    this.scroll.scrollToElement(element)
                }
            }
        }

    }
</script>

<style lang="stylus" scoped>
    @import "~styles/varibles.styl"
    .border-topbottom
    &:before
        border-color: #ccc
    &:after
        border-color: #ccc
    .border-bottom
        &:before
            border-color: #ccc
    .list
        overflow: hidden
        position: absolute
        top: 1.58rem
        left: 0
        right: 0
        bottom: 0
        .title
            line-height: .54rem
            background: #eee
            padding-left: .2rem
            color: #666
            font-size: .26rem
        .button-list
            overflow: hidden
            padding: .1rem .6rem .1rem .1rem
            .button-wrapper
                float: left
                width: 33.33%
                .button
                    margin: .1rem
                    padding: .1rem 0
                    text-align: center
                    border: .02rem solid #ccc
                    border-radius: .06rem
        .item-list
            .item
                line-height: .76rem
                padding-left: .2rem
</style>
