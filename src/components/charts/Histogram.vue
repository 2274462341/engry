<template>
  <div id="Histogram"></div>
</template>

<script>
var xData = [
  "1月",
  "2月",
  "3月",
  "4月",
  "5月",
  "6月",
  "7月",
  "8月",
  "9月",
  "10月",
  "11月",
  "12月"
];
var y1Data = [178, 290, 270, 230, 185, 230, 185, 130, 80, 70, 90, 175];
var y2Data = [14, 17, 13, 19, 16, 18, 8, 11, 4, 2.5, 2, 18];
var y3Data = [30, 38.12, 15.9, 10.9, 0.7, 11.1, 12.1, 15, 20, 18, 9, 8];

let echarts = require("echarts");
export default {
  mounted() {
    var Histo = echarts.init(document.getElementById("Histogram"));
    Histo.setOption({
      grid: {
        left: "7%",
        right: "5%",
        top: "10%",
        bottom: "10%"
      },
      title: {
        show: false
      },
      tooltip: {
        trigger: "axis",
        axisPointer: {
          // 坐标轴指示器，坐标轴触发有效
          type: "line" // 默认为直线，可选为：'line' | 'shadow'
        },
         textStyle: {
          align: "left"
        }
      },
      legend: {
        data: ["监控数量", "监控密度", "增长%"],
        right: "3%",
        top: "1",
        itemWidth: 11,
        itemHeight: 11,
        textStyle: {
          color: "#ffffff",
          fontSize: 14
        }
      },
      toolbox: {
        show: false
      },
      xAxis: [
        {
          type: "category",
          boundaryGap: true,
          show: true,
          axisTick: {
            show: false
          },
          axisLabel: {
            fontSize: 12,
            color: "#d0d0d0",
            margin: 12,
            interval: 0,
            formatter: function(val) {
              return val;
            }
          },
          axisLine: {
            lineStyle: {
              type: "dashed",
              color: "#4e608b", //左边线的颜色
              width: "1" //坐标线的宽度
            }
          },
          data: xData
        }
      ],
      yAxis: [
        {
          type: "value",
          scale: true,
          name: "",
          axisLine: {
            show: false
          },
          splitNumber: 4,
          axisTick: {
            show: false
          },
          splitLine: {
            lineStyle: {
              // 使用深浅的间隔色
              color: "#4e608b"
            }
          },
          axisLabel: {
            fontSize: 13,
            color: "#d0d0d0",
            margin: 12
          },
          max: 300,
          min: 0,
          boundaryGap: [0.2, 0.2]
        },
        {
          type: "value",
          scale: true,
          axisLine: {
            show: false
          },
          splitNumber: 3,
          axisTick: {
            show: false
          },
          axisLabel: {
            fontSize: 13,
            color: "#d0d0d0",
            margin: 12
          },
          splitLine: {
            lineStyle: {
              // 使用深浅的间隔色
              color: "#4e608b"
            }
          },
          name: "",
          max: 60,
          min: 0,
          boundaryGap: [0.2, 0.2]
        }
      ],
      series: [
        {
          name: "监控数量",
          type: "bar",
          label: {
            normal: {
              // show: true,
              position: "top",
              textStyle: {
                color: "#1dacfe"
              }
            }
          },
          itemStyle: {
            normal: {
              color: new echarts.graphic.LinearGradient(
                0,
                1,
                0,
                0,
                [
                  {
                    offset: 0,
                    color: "#ea2407" // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "#fe8b3b" // 100% 处的颜色
                  }
                ],
                false
              )
            }
          },
          barWidth: "30%",
          yAxisIndex: 0,
          backgroundColor: "red",
          data: y1Data
        },
        {
          name: "监控密度",
          yAxisIndex: 1,
          color: "#ffd300",
          label: {
            normal: {
              show: true,
              position: "top",
              textStyle: {
                color: "#ffd300"
              }
            }
          },
          lineStyle: {
            color: "rgb(233,23,0)"
          },
          type: "line",
          data: y2Data
        },
        {
          name: "增长%",
          yAxisIndex: 1,
          color: "#ffd300",
          label: {
            normal: {
              show: true,
              position: "top",
              textStyle: {
                color: "#ffd300"
              }
            }
          },
          lineStyle: {
            color: "rgb(255,145,62)"
          },
          type: "line",
          data: y3Data
        }
      ]
    });
  }
};
</script>

<style>
#Histogram {
  width: 90%;
  height: 300px;
  margin-top: 10px;
}
</style>
