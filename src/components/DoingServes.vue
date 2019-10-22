<template>
  <div class="doing">
    <div class="doing-head">
      <div class="doing-head-title">营业厅服务</div>
      <div class="doing-head-title">网络化服务</div>
    </div>
    <div class="doing-main">
      <div class="doing-main-left">
        <div class="client-main-title">
          <span>| 办 电 概 括</span>
          <strong>当年</strong>
        </div>
        <div class="doing-main-charts">
          <div class="main-charts">
            <div class="main-charts-top">
              <div class="charts-list">
                <div>
                  <span class="big">60</span>
                  <span class="small">%</span>
                </div>
                <div class="line">线上办电率</div>
                <div>电压</div>
              </div>
            </div>
            <div class="main-charts-top">
              <div class="charts-list">
                <div>
                  <span class="big">60</span>
                  <span class="small">%</span>
                </div>
                <div class="line">线上办电率</div>
                <div>电压</div>
              </div>
            </div>
            <div class="main-charts-bottom">
              <Day></Day>
            </div>
          </div>
          <div class="annulus">
            <Annulus></Annulus>
          </div>
        </div>
      </div>

      <div class="doing-main-right">
        <div class="client-main-title">| 重 要 客 户</div>
        <div class="list">
          <span>序 号</span>
          <span>营 业 厅 名 称</span>
          <span>业 务 总 量</span>
          <span>微 信 预 定 量</span>
        </div>
        <!-- 表格 -->
        <div class="aa">
          <el-scrollbar style="height:100%">
            <ul class="client-main-table">
              <li v-for="(item,index) in arr" :key="index">
                <span>{{item.num}}</span>
                <span>{{item.title}}</span>
                <span>{{item.gross}}</span>
                <span>{{item.probably}}</span>
              </li>
            </ul>
          </el-scrollbar>
        </div>
        <div class="doing-charts">
          <p>重要客户数/位</p>
          <Histograms></Histograms>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Histograms from "./charts/Histograms";
import Day from "./charts/Day";
import Annulus from "./charts/Annulus";
import "./css/doing.css";
import "./css/clientLeft.css";
export default {
  name: "",
  data() {
    return {
      arr: [
        { num: 1, title: "乌鲁木齐开发区营业厅", gross: 230, probably: 16 },
        { num: 2, title: "乌鲁木齐开发区营业厅", gross: 210, probably: 26 },
        { num: 3, title: "乌鲁木齐开发区营业厅", gross: 130, probably: 36 },
        { num: 4, title: "乌鲁木齐开发区营业厅", gross: 250, probably: 56 },
        { num: 5, title: "乌鲁木齐开发区营业厅", gross: 209, probably: 66 },
        { num: 6, title: "乌鲁木齐开发区营业厅", gross: 310, probably: 78 },
        { num: 7, title: "乌鲁木齐开发区营业厅", gross: 270, probably: 45 },
        { num: 8, title: "乌鲁木齐开发区营业厅", gross: 540, probably: 45 },
        { num: 9, title: "乌鲁木齐开发区营业厅", gross: 170, probably: 45 },
        { num: 10, title: "乌鲁木齐开发区营业厅", gross: 200, probably: 45 }
      ]
    };
  },
  methods: {},
  components: {
    Histograms,
    Day,
    Annulus
  }
};
</script>

<style scoped="scoped">
</style>
