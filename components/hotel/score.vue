<template>
    <div class="main">
        <!-- canvas不能用样式来写，必须用属性 -->
        <canvas id="cavans" width="300" height="300"></canvas>
    </div>
</template>

<script>
export default {
    props: ["score"],
    mounted(){
        var c = document.getElementById("cavans");
        // 获取画笔
        var ctx = c.getContext("2d");
        // 给画笔添加颜色
        ctx.strokeStyle = "red";
        // 设置画笔宽度
        ctx.lineWidth = 3;
        // 开始绘制“当前”的路径
        ctx.beginPath();
        // 绘制圆形 (重点在怎样把角度换算成弧度)
        ctx.arc(
            150,150,100, -90 * Math.PI/180, 
            Math.PI/180 * (360 * (this.score / 10)) - (90 * Math.PI/180)
        );
        // 闭合当前的图形
        ctx.stroke();
    }
};
</script>

<style scoped>
.main{
    width:300px;
    height:300px;
    border: 1px #ddd solid;
    margin:0 auto;
}
</style>