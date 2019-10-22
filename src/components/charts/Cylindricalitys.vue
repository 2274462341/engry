 <template>
  <div id="chart"></div>
</template>

<script>
let echarts = require("echarts");
var data = [115, 170];
var sum = 0;
var percentdata = [];
for (var i = 0; i < data.length; i++) {
  sum += data[i];
}
for (var j = 0; j < data.length; j++) {
  percentdata.push(data[j]) ;
}
export default {
  data() {
    return {};
  },

  mounted() {
    /*ECharts图表*/
    var myChart = echarts.init(document.getElementById("chart"));
    myChart.setOption({
      color: ["#0d6dff","#21c15d"],
      grid: {
        left: "8",
        right: "10",
        top: "12",
        bottom: "18",
        containLabel: true
      },
      yAxis: {
        color: ["white"],
        data: ["用车是", "SQ测恶"],
        axisTick: {
          show: false
        },
        axisLabel: {
          textStyle: {
            color: "#74b0e4"
          }
        }
      },

      xAxis: [
        {
          axisTick: {
            show: false
          },
          type: "value",
          max: 250,
          splitNumber: 5,
          axisLabel: {
            formatter: "{value}",
            textStyle: {
              color: "#74b0e4"
            }
          }
        }
      ],
      series: [
        {
          name: "销量",
          type: "bar",
          barWidth: "20",
          label: {
            normal: {
              show: true,
              position: "right",
              formatter: "{c}",
              textStyle: {
                color: "#74b0e4"
              }
            }
          },
          data: percentdata
        }
      ]
    });
  }
};
</script>
<style scoped>
#chart {
  width: 320px;
  height: 300px;
}
</style>

