<template>
    <div style="padding: 100px;">
        <div id="container"></div> 
        <div id="panel"></div>
    </div>
</template>

<script>
export default {
    mounted(){
        
        var url = 'https://webapi.amap.com/maps?v=1.4.15&key=0e50af054087c7bec2bd57e4356a4bd3&callback=onLoad';
        var jsapi = document.createElement('script');
        jsapi.charset = 'utf-8';
        jsapi.src = url;
        document.head.appendChild(jsapi);

        window.onLoad  = function(){
            var map = new AMap.Map('container', {
                resizeEnable: true
            });

            // 文档地址：https://lbs.amap.com/api/javascript-api/example/poi-search/around-search
            AMap.service(["AMap.PlaceSearch"], function() {
                //构造地点查询类
                var placeSearch = new AMap.PlaceSearch({ 
                    type: '交通设施服务', // 兴趣点类别
                    pageSize: 5, // 单页显示结果条数
                    pageIndex: 1, // 页码
                    city: "广州", // 兴趣点城市
                    citylimit: true,  //是否强制限制在设置的城市内搜索
                    map: map, // 展现结果的地图实例
                    panel: "panel", // 结果列表将在此容器中进行展示。
                    autoFitView: true // 是否自动调整地图视野使绘制的 Marker点都处于视口的可见范围
                });
                
                var cpoint = [113.3245904, 23.1066805]; //中心点坐标
                placeSearch.searchNearBy('', cpoint, 2000, function(status, result) {

                });
            });
        }
    }
};
</script>

<style>
#container{
    width: 500px;
    height: 500px;
}

 #panel {
    position: fixed;
    background-color: white;
    max-height: 90%;
    overflow-y: auto;
    top: 200px;
    right: 10px;
    width: 280px;
    border-bottom: solid 1px silver;
}
</style>