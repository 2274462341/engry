<template>
  <div id="chartdivs"></div>
</template>

<script>
let echarts = require("echarts");
export default {
  mounted() {
    var myCharts = echarts.init(document.getElementById("chartdivs"));
    myCharts.setOption({
      color: ["#003366", "#006699", "#4cabce", "#e5323e"],
      tooltip: {
        trigger: "item",
        formatter: '<img src="'+require('../../imgs/icon/icon_8.png')+'" style="width:20px;height:20px;margin-right:5px;margin-top:5px" />{b}<br/><img src="'+require('../../imgs/icon/icon_5.png')+'" style="width:20px;height:20px;margin-right:5px;margin-top:4px" />{c}<span style="fontSize:10">kwh</span>',
        extraCssText: `background:#2b497d;width:120px;height:60px;line-height:30px`,
        textStyle: {
          align: "left"
        }
      },
      toolbox:{
       feature:{
         mark:{show:true}
       }
      },
      title: {
        text: "用电量占比",
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
        data: ["一般工商业", "居民照明", "大工业", "农民"],
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
          color: ["#17c1e4", "#7bde60", "#8423ff", "#f7b431"],
          data: [
            { value: 335, name: "一般工商业" },
            { value: 310, name: "居民照明" },
            { value: 234, name: "大工业" },
            { value: 135, name: "农民" }
          ]
        }
      ]
    });
  }
};
</script>

<style>
#chartdivs {
  height: 350px;
  width: 100%;
}
</style>
