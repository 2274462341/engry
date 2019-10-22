<template>
  <div class="header">
    <i class="bg-1"></i>
    <i class="bg-2"></i>
    <i class="bg-3"></i>
  </div>
</template>

<script>
export default {
  name: "",
  data() {
    return {};
  },
  methods: {}
};
</script>

<style scoped>
.header {
  height: 65px;
  width: 100%;
  display: flex;
  /* position: relative; */
}

.bg-1 {
  width: 111.3%;
  height: 40px;
  background-image: url("../imgs/bg_副标题1.png");
  background-size: 100% 100%;
  position: absolute;
  left: 5.5%;
  top: 30px;
}
.bg-2 {
  width: 30%;
  height: 40px;
  background-size: 100% 100%;
  background-image: url("../imgs/bg_主标题1.png");
  margin-right: 55px;
  margin-top: 30px;
  position: absolute;
  left: 116.3%;
  top: 0px;
}
.bg-3 {
  width: 115.4%;
  height: 40px;
  background-size: 100% 100%;
  background-image: url("../imgs/bg_副标题2.png");
  position: absolute;
  left: 145.8%;
  top: 30px;
}
</style>
