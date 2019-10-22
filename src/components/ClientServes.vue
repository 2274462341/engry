<template>
  <div class="client">
    <div class="client-head">
      <div class="client-head-title">营业厅服务</div>
      <div class="client-head-title">网络化服务</div>
      <div class="client-head-title">重要用户服务</div>
    </div>
    <div class="client-main">
      <div class="client-main-left">
        <div class="client-main-title">| 营 业 厅</div>
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
        <div class="client-main-bottom">
          <div class="client-bottom-top">
            <div class="client-bottom-title">
              <span>| 业 务 办 理</span>
              <div class="time">
                <strong>当日</strong>
                <strong>当月</strong>
                <strong>当年</strong>
              </div>
            </div>
            <div class="client-bottom-title">
              <span>| 业 务 办 理</span>
              <strong>当日</strong>
            </div>
          </div>
          <div class="client-bottom-tit">某某营业厅名称</div>
          <div class="client-bottom-chart">
            <div class="a">
              <Cylindricality></Cylindricality>
            </div>
            <div class="b">
              <Cylindricalitys></Cylindricalitys>
            </div>
          </div>
        </div>
      </div>
      <div class="client-main-right">
        <div class="client-main-title">
          <span>| 电 费 收 取</span>
          <div class="time">
            <strong>当日</strong>
            <strong>当月</strong>
            <strong>当年</strong>
          </div>
        </div>
        <div class="client-bottom-tit">某某营业厅名称</div>

        <div class="client-right-money">
          <Count></Count>
        </div>

        <div class="client-right-video">
          <div class="client-main-title">| 视 频 影 像</div>
          <div class="client-bottom-tit">某某营业厅名称</div>
          <div class="right-content">
            <div class="right-left">
              <div class="right-list">
                <span>序 号</span>
                <span>摄 像 描 述</span>
              </div>
              <div class="menu">
                <el-scrollbar style="height:100%">
                  <ul class="client-right-table">
                    <li v-for="(item,index) in str" :key="index">
                      <span>{{item.num}}</span>
                      <span>{{item.title}}</span>
                    </li>
                  </ul>
                </el-scrollbar>
              </div>
            </div>

            <div class="right-right">
              <div class="right-picture" v-for="(item,index) in data" :key="index">
                <div class="backpicture">
                  <img :src="item.img" alt />
                </div>
                <div class="right-tit">
                  <span>{{item.time}}</span>
                  <span>{{item.title}}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Cylindricality from "./charts/Cylindricality";
import Cylindricalitys from "./charts/Cylindricalitys";
import Clientcss from "./css/clientLeft.css";
import "./css/demo.css";
import Count from "./vue-count";
import img1 from "../imgs/1.png";
import img2 from "../imgs/2.png";
import img3 from "../imgs/3.png";
import img4 from "../imgs/4.png";

export default {
  name: "",
  data() {
    return {
      data: [
        { img: img1, time: "2019-6-26 10:18:05", title: "某某营业厅柜台A" },
        { img: img2, time: "2019-6-26 10:18:05", title: "某某营业厅柜台B" },
        { img: img3, time: "2019-6-26 10:18:05", title: "某某营业厅柜台C" },
        { img: img4, time: "2019-6-26 10:18:05", title: "某某营业厅柜台D" }
      ],
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
      ],
      str: [
        { num: 1, title: "出入口" },
        { num: 2, title: "大厅" },
        { num: 3, title: "公共区A" },
        { num: 4, title: "公共区B" },
        { num: 5, title: "公共区C" },
        { num: 6, title: "公共区D" },
        { num: 7, title: "走廊A" },
        { num: 8, title: "走廊B" },
        { num: 9, title: "走廊C" },
        { num: 10, title: "楼梯" }
      ]
    };
  },

  methods: {},
  components: {
    Cylindricality,
    Cylindricalitys,
    Count
  }
};
</script>

<style scoped>
</style>
