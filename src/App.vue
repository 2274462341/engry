<template>
  <div id="app">
    <div class="head">
      <Header></Header>
      <div class="head-position">
        <p class="bg1-position">客户服务</p>
        <p class="bg2-position">电量电费</p>
        <p class="bg3-position">营商环境</p>
        <!-- <p class="bg2-position">电量电费</p> -->
      </div>
    </div>

    <div class="main">
      <div class="map">
        <Map></Map>
      </div>
      <div class="power">
        <Client></Client>
      </div>
      <div class="power">
        <Power></Power>
      </div>
      <div class="power">
        <Doing></Doing>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Client from "./components/ClientServes";
import Power from "./components/PowerServes";
import Doing from "./components/DoingServes";
import Map from './components/charts/Map'
export default {
  name: "App",
  components: {
    Header,
    Client,
    Power,
    Doing,
    Map
  }
};
</script>

<style>
* {
  list-style: none;
  color: #fff;
}
.el-scrollbar__wrap {
  overflow-x: hidden;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 5030px;
  height: 900px;
  background-image: url("./imgs/区域背景2.png");
  background-size: 100% 100%;
}
.head {
  width: 100%;
  height: 60px;
}
.head-position {
  position: relative;
  display: flex;
}
.bg1-position {
  position: absolute;
  top: -53px;
  left: 27.6%;
  font-size: 20px;
  word-spacing: 8px;
  letter-spacing: 6px;
}
.bg2-position {
  position: absolute;
  top: -53px;
  right: 34.7%;
  font-size: 20px;
  word-spacing: 8px;
  letter-spacing: 6px;
}
.bg3-position {
  position: absolute;
  top: -53px;
  right: 13.4%;
  font-size: 20px;
  word-spacing: 8px;
  letter-spacing: 6px;
}
.main {
  width: 100%;
  height: 800px;
  display: flex;
  justify-content: space-between;
}

.map {
  width: 12.3%;
  height: 821px;
  margin-left: 102px;
}
.power {
  width: 28%;
  height: 821px;
  margin-right: 10px;
  /* margin-top: 5px; */
}
</style>
