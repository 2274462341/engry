<template>
  <div id="chartdiv"></div>
</template>

<script>
let echarts = require("echarts");

export default {
  mounted() {
    var myChart = echarts.init(document.getElementById("chartdiv"));
    myChart.setOption({
      tooltip: {
        trigger: "item",
        formatter: '<img src="'+require('../../imgs/icon/icon_8.png')+'" style="width:20px;height:20px;margin-right:5px;margin-top:5px" />{b}<br/><img src="'+require('../../imgs/icon/icon_5.png')+'" style="width:20px;height:20px;margin-right:5px;margin-top:4px" />{c}<span style="fontSize:10">kwh</span>',
        extraCssText: `background:#2b497d;width:120px;height:60px;line-height:30px`,
        textStyle: {
          align: "left",
          height:30
        }
      },
      title: {
        text: "售电量占比",
        x: "center",
        y: "310px",
        textStyle: {
          color: "#fff",
          fontWeight: "bolder",
          fontSize: 16
        }
      },
      legend: {
        orient: "vertical",
        x: "80%",
        y: "20px",
        data: [
          "某某单位名称1",
          "某某单位名称2",
          "某某单位名称3",
          "某某单位名称4"
        ],
        itemWidth: 15,
        itemHeight: 15,
        textStyle: {
          color: "#fff"
        },
        itemGap: 20
      },
      series: [
        {
          name: "访问来源",
          type: "pie",
          radius: ["30%", "60%"],
          avoidLabelOverlap: false,

          label: {
            normal: {
              show: true,
              position: "inner",
              formatter: "{d}%"
            },
            emphasis: {
              show: true
            }
          },
          labelLine: {
            normal: {
              show: false
            }
          },
          color: ["#17c1e4", "#8423ff", "#7bde60", "#f7b431"],
          data: [
            { value: 335, name: "某某单位名称1" },
            { value: 310, name: "某某单位名称2" },
            { value: 234, name: "某某单位名称3" },
            { value: 135, name: "某某单位名称4" }
          ]
        }
      ]
    });
  }
};
</script>

<style>
#chartdiv {
  height: 350px;
  width: 100%;
}
.icon{
  width:30px;
  height: 30px;
  background-image: url("../../imgs/icon/icon_8.png");
  background-size: 100%;
}
</style>
