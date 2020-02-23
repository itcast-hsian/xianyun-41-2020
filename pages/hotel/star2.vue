<template>
    <div style="margin: 100px auto; width:300px;">
        <!-- 底层的div -->
        <div class="main">
            <div class="content" ref="content" @click="handleClick">
                <div class="bottom" ref="bottom">
                    <span 
                    class="iconfont iconhuangguan" 
                    v-for="item in 5" 
                    :key="item">
                    </span>
                </div>

                <!-- up-wrap控制宽度,超出部分就隐藏 -->
                <div class="up-wrap" :style="`width:${upWidth}px;`">
                    <!-- 永远都是展示出5颗星星 -->
                    <div class="up" ref="up">
                        <span 
                        class="iconfont iconhuangguan" 
                        v-for="item in 5" 
                        :key="item">
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            // 5颗星星的宽度
            width: 0,
            upWidth: 0
        };
    },
    mounted() {
        // 5颗星星的宽度
        this.width = this.$refs.bottom.offsetWidth;
        // 给content赋值宽度
        this.$refs.content.style.width = this.width + 'px';
    },

    methods: {
        handleClick(e){
            // e.offsetX鼠标点击的位置
            this.upWidth = e.offsetX; 

            // 当前的评分
            const score = e.offsetX / this.width * 5;
        }
    }
};
</script>

<style scoped lang="less">
.main {
    position: relative;
    height: 300px;
}

.content{
    position: absolute;
    left:0; top:0;
    height:20px;
}

.bottom {
    position: absolute;
    left: 0;
    top: 0;
}

.up-wrap{
    position: absolute;
    left: 0;
    top: 0;
    overflow: hidden;
    height: 20px;
}

.up {
    position: absolute;
    left: 0;
    top: 0;
    z-index: 2;
    span {
        color: red;
    }
}
</style>