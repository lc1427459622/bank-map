<template>
  <div class="hello">
    <div id="map" class="container"></div>
  </div>
</template>

<script>
import 'maptalks/dist/maptalks.css';
import * as maptalks from 'maptalks';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted() {
    this.$nextTick(() => {
      const map = new maptalks.Map('map', {
        center: [114.063885, 22.524395],
        zoom: 14,
        // 默认主题
        baseLayer: new maptalks.TileLayer('base', {
          urlTemplate: 'http://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png',
          subdomains: ['a', 'b', 'c', 'd'],
          attribution: '&copy; <a href="http://osm.org">OpenStreetMap</a> contributors, &copy; <a href="https://carto.com/">CARTO</a>',
        }),
        // 百度地图图层
        // minZoom:1,
        // maxZoom:19,
        // spatialReference:{
        //   projection : 'baidu'
        // },
        // baseLayer: new maptalks.TileLayer('base', {
        //   'urlTemplate' : 'https://gss{s}.bdstatic.com/8bo_dTSlRsgBo1vgoIiO_jowehsv/tile/?qt=tile&x={x}&y={y}&z={z}&styles=pl&scaler=1&udt=20170927',
        //   'subdomains':[0, 1, 2, 3],
        //   'attribution' :  '&copy; <a target="_blank" href="http://map.baidu.com">Baidu</a>'
        // })
      });
      // var marker = new maptalks.Marker(
      //   map.getCenter(),
      //   {
      //     symbol : {
      //       'textName' : 'Layer is shown.', // 文本描述
      //       'textWeight' : 'bold', // 自提加粗
      //       'textSize' : 50, // 字体大小
      //       'textFill' : '#1bbc9b', // 字体填充颜色
      //       'textHaloFill' : '#fff', // 字体颜色
      //       'textHaloRadius' : 5, // 削圆角
      //     }
      //   }
      // );
      // var layer = new maptalks.VectorLayer('vector', [marker]).addTo(map);

      // 默认弹层
      // var layer = new maptalks.VectorLayer('vector').addTo(map);
      // var marker = new maptalks.Marker([114.063885, 22.524395]).addTo(layer);
      // marker.setInfoWindow({
      //   'title'     : 'BANK-MAP',
      //   'content'   : '你点个试试!'
      //   // 'autoPan': true,
      //   // 'width': 300,
      //   // 'minHeight': 120,
      //   // 'custom': false,
      //   //'autoOpenOn' : 'click',  //set to null if not to open when clicking on marker
      //   //'autoCloseOn' : 'click'
      // });
      // marker.openInfoWindow();

      // 自定义信息弹层
      var coordinate = map.getCenter().toFixed(3);
      var infoWindow = new maptalks.ui.InfoWindow({
        'title'     : 'BANK-MAP',
        'content'   : '你点个试试!'
        // 'autoPan': true,
        // 'width': 300,
        // 'minHeight': 120,
        // 'custom': false,
        //'autoOpenOn' : 'click',  //set to null if not to open when clicking on marker
        //'autoCloseOn' : 'click'
      });
      infoWindow.addTo(map).show(coordinate);

      // console.log('map: ', map);
    });
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  width:98%;
  height:97%;
  text-align: center;
  overflow: hidden;
  padding: 10px;
}
.container{
  width:100%;
  height:100%;
  margin: 0 auto;
}
.content {
  color:#fff;
  width:190px;
  height:128px;
  /* background-color:#051127; */
  background: coral;
  border:1px solid #0c2c45;
}
.pop_title {
  float:left;
  padding-left:10px;
  width:180px;height:36px;
  line-height:36px;
  /* background:url(title.png); */
  font-weight:bold;font-size:16px;
}
.pop_time{
  float:left;
  width:183px;
  height:30px;
  margin:0 10px;
  line-height:36px;
}
.pop_dept {
  float:left;
  padding:5px;
  max-width:65px;
  line-height:15px;
  text-align:center;
  border:1px solid #192b41;
  margin:0 10px;
}
.pop_arrow{
  float:left;
  width:15px;
  height:24px;
  line-height:24px;
  /* background:url(arrow.png) no-repeat center center */
}
.arrow{
  display:block;
  width:17px;
  height:10px;
  /* background:url(em.png) no-repeat; */
  position:absolute;
  left:50%;margin-left:-5px;bottom:-10px;
}
/* .content{color:#fff;width:190px;height:128px;background-color:#051127;border:1px solid #0c2c45}
.pop_title{float:left;padding-left:10px;width:180px;height:36px;line-height:36px;background:url(title.png);font-weight:bold;font-size:16px}
.pop_time{float:left;width:183px;height:30px;margin:0 10px;line-height:36px}
.pop_dept{float:left;padding:5px;max-width:65px;line-height:15px;text-align:center;border:1px solid #192b41;margin:0 10px}
.pop_arrow{float:left;width:15px;height:24px;line-height:24px;background:url(arrow.png) no-repeat center center}
.arrow{display:block;width:17px;height:10px;background:url(em.png) no-repeat;position:absolute;left:50%;margin-left:-5px;bottom:-10px} */
</style>
