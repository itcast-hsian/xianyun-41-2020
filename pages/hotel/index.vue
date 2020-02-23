<template>
    <div style="padding: 100px;">
        酒店首页
        <h2>评分</h2>
        <Score :score="8.5"/>
    </div>
</template>

<script>
import Score from "@/components/hotel/score";
export default {
    components: {
        Score
    }
};
</script>

<style>
</style>