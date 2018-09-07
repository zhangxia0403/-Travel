<template>
    <ul class="list">
        <li
                class="item"
                v-for="item of letters"
                :key="item"
                :ref="item"
                @touchstart="handleTouchStart"
                @touchmove="handleTouchMove"
                @touchend="handleTouchEnd"
                @click="handleLetterClick"
        >
            {{item}}
        </li>
    </ul>
</template>

<script>
    export default {

        name: 'CityAlphabet',
        props:{
            cities: Object
        },
        data(){
            return {
                touchStatus: false,
                startY: 0,
                timer: null
            }
        },
        computed:{
            letters () {
                const letters = [];
                // 遍历对象，循环的是key值
                for(var i in this.cities){
                    // 将循环的key值，存在一个数组里
                    letters.push(i)
                }
                return letters
            }
        },
        updated() {
            // 获取A距离顶部的距离
            this.startY = this.$refs['A'][0].offsetTop;
        },
        methods:{
            handleLetterClick (e) {
                // 子组件向父级传递数据，通过 $emit 向上传递
                this.$emit('change',e.target.innerText)
            },
            handleTouchStart () {
                this.touchStatus = true
            },
            handleTouchMove (e) {
                if(this.touchStatus){

                    // 函数截流
                    if(this.timer){
                        clearTimeout(this.timer)
                    }
                    this.timer = setTimeout(() => {
                        const touchY = e.touches[0].clientY - 79;
                        const index = Math.floor((touchY - this.startY)/20);
                        if(index >= 0 && index < this.letters.length){
                            this.$emit('change',this.letters[index])
                        }
                    },16)

                }
            },
            handleTouchEnd () {
                this.touchStatus = false
            }
        },
        mounted () {

        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    .list
        /*垂直居中*/
        display: flex
        flex-direction: column
        justify-content: center
        position: absolute
        top: 1.58rem
        right: 0
        bottom: 0
        width: .4rem
        .item
            line-height: .4rem
            text-align: center
            color: $bgColor
</style>
