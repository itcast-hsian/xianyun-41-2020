<template>
    <div style="margin: 100px auto; width:300px;">
        <!-- 底层的div -->
        <div class="main">
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

        // 假设接口返回了3.5分
        this.upWidth = (3.5 / 5) * this.width;
        
    }
};
</script>

<style scoped lang="less">
.main {
    position: relative;
    height: 300px;
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