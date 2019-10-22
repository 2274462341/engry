<template>
  <div class="count-box">
    <div class="count-tit">
      <div class="client-right-collect">
        <p>电费收取量/万元</p>
        <p>坐收</p>
      </div>
      <div class="client-right-collect">
        <p>电费收取量/万元</p>
        <p>坐收</p>
      </div>
    </div>
<div class="count-number">
   <div class="as" v-for="(item, index) in endVal" :key="index">
      <div class="numberback"></div>
      <div class="numberback"></div>
      <div class="numberback"></div>
      <div class="numberback"></div>
      <div class="numberback"></div>
      <div class="numberback"></div>
      <countTo class="moneySize" :startval="startVal" :endVal="item.num" :duration="3000"></countTo>
    </div>
</div>
   
  </div>
</template>

<script>
import countTo from "vue-count-to";
import "../assets/styles/index.css"
export default {
  name: "",
  data() {
    return {
      startVal: 0,
      endVal: [
        { num: "82345" },
        { num: "22345" },
        { num: "32345" },
        { num: "42345" }
      ]
    };
  },
  methods: {},
  components: { countTo }
};
</script>

<style scoped>
.count-box{
  width:100%;
}
.count-number{
  display: flex;
  flex-wrap: wrap;
}
.count-tit{
  width:100%;
  height: 80px;

}
.client-right-collect{
  width:50%;
  text-align: left;
  padding-left: 10px;
}
.as {
  display: flex;
  position: relative;
  margin: 3px 15px 40px 15px;
  width:45%;
}

.numberback {
  width: 45px;
  height: 80px;
  background-image: url("../imgs/数字背景.png");
  background-size: 45px 80px;
  margin: 0 5px;
}
.moneySize {
  font-size: 52px;
  word-spacing: 2px;
  letter-spacing: 26px;
  position: absolute;
  left: 9px;
  top: 6px;
  color: #fefefe;
  font-family: 'lcdd';
}

.count-tit{
  display: flex;
  justify-content:space-around;
}
</style>
