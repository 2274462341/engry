<template>
  <div class="powermain">
    <div class="power-head">
      <div class="power-head-title">营业厅服务</div>
      <div class="power-head-title">网络化服务</div>
      <div class="power-head-title">营业厅服务</div>
      <div class="power-head-title">网络化服务</div>
    </div>
    <div class="power-main">
      <div class="power-main-left">
        <div class="power-bottom-title">| 告 电 量</div>
        <div class="power-over">
          <div class="power-over-left">
            <div class="power-posi">
              <span class="sizes">14.25</span>
              <span>万/KWh</span>
            </div>
          </div>
          <div class="power-over-right">
            <div class="power-posi">
              <span class="sizes">356.2</span>
              <span>万/KWh</span>
            </div>
          </div>
        </div>
        <div class="power-span">
          <b>当月售电量</b>
          <b>累计售电量</b>
        </div>
        <div class="power-bigbar">
          <p>告电量/万KWh</p>
          <Histogram></Histogram>
        </div>
      </div>
      <div class="power-main-right">
        <div class="power-bottom-title">| 告 电 统 计</div>
        <div class="power-charts">
          <PiechartTop></PiechartTop>
          <PiechartBottom></PiechartBottom>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Histogram from "./charts/Histogram";
import PiechartTop from "./charts/PiechartTop";
import PiechartBottom from "./charts/PiechartBottom";
import "./css/power.css";
import '../assets/styles/index.css'
export default {
  name: "",
  data() {
    return {};
  },
  methods: {},
  components: {
    Histogram,
    PiechartTop,
    PiechartBottom
  }
};
</script>

<style scoped="scoped">
</style>
