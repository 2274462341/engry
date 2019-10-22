<template>
  <div>
    <div class="canvas-box">
      <canvas id="canvas"></canvas>
      <div class="size">平均接电时间 (低压)</div>
      <div class="day-posit">
        <b>5</b>
        <span>天</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    this.initCanvas();
  },
  methods: {
    initCanvas() {
      let canvas = document.getElementById("canvas");
      let ctx = canvas.getContext("2d");
      let winW = canvas.parentNode.offsetWidth;
      let winH = canvas.parentNode.offsetHeight;
      let deg = Math.PI / 180;
      canvas.width = winW;
      canvas.height = winH;

      let x = winW / 2;
      let y = winH / 2;
      let initArr = [];

      var gradient = ctx.createLinearGradient(
        x - x * 0.5,
        y - x * 0.5,
        x + x * 0.5,
        y + x * 0.5
      );
      gradient.addColorStop(0, "#13e9ff");
      gradient.addColorStop(1, "#0f9fff");

      const dragArc = (x, y, r, s, e, flag) => {
        ctx.arc(x, y, r, s * deg, e * deg, flag);
      };

      const initDrag = initArr => {
        initArr.forEach(item => {
          ctx.beginPath();
          item();
          ctx.stroke();
          ctx.closePath();
        });
      };

      function bigArc() {
        ctx.lineWidth = "2";
        dragArc(x, y, x * 0.6, 0, 360);
        ctx.strokeStyle = "#2f5294";
      }

      initArr.push(bigArc);

      function radianOne() {
        ctx.lineWidth = "2";
        dragArc(x, y, x * 0.55, -50, -90, true);
        ctx.lineTo(
          Math.cos(-90 * deg) * x * 0.8 + x,
          Math.sin(-90 * deg) * y * 0.8 + y
        );
        dragArc(x, y, x * 0.8, -90, -40);
        ctx.strokeStyle = "#18c0ff";
      }

      initArr.push(radianOne);

      function radianTwo() {
        ctx.lineWidth = "2";
        ctx.moveTo(
          Math.cos(50 * deg) * x * 0.6 + x,
          Math.sin(50 * deg) * y * 0.6 + y
        );
        dragArc(x, y, x * 0.8, 50, 90);
        ctx.lineTo(
          Math.cos(90 * deg) * x * 0.6 + x,
          Math.sin(90 * deg) * y * 0.6 + y
        );
        ctx.strokeStyle = "#18c0ff";
      }

      initArr.push(radianTwo);

      function radianThree() {
        ctx.lineWidth = "2";
        ctx.moveTo(
          Math.cos(130 * deg) * x * 0.6 + x,
          Math.sin(130 * deg) * y * 0.6 + y
        );
        dragArc(x, y, x * 0.8, 130, 220);
        ctx.lineTo(
          Math.cos(220 * deg) * x * 0.6 + x,
          Math.sin(220 * deg) * y * 0.6 + y
        );
        ctx.strokeStyle = "#18c0ff";
      }

      initArr.push(radianThree);

      initDrag(initArr);

      ctx.beginPath();
      ctx.lineWidth = x * 0.06;
      ctx.arc(x, y, x * 0.44, 0 * deg, 360 * deg);
      ctx.strokeStyle = "#2f5294";
      ctx.stroke();
      ctx.closePath();

      ctx.beginPath();
      ctx.lineWidth = x * 0.06;
      ctx.lineCap = "round";
      ctx.arc(x, y, x * 0.44, 0 * deg, 270 * deg);
      ctx.strokeStyle = gradient;
      ctx.stroke();
      ctx.closePath();

      for (let i = 0; i < 8; i++) {
        ctx.beginPath();
        ctx.lineWidth = x * 0.12;
        ctx.lineCap = "butt";
        ctx.arc(x, y, x * 0.57, (55 + i * 20) * deg, (70 + i * 20) * deg);
        ctx.strokeStyle = "gradient";
        ctx.stroke();
        ctx.closePath();
      }

      for (let i = 0; i < 4; i++) {
        ctx.beginPath();
        ctx.arc(
          Math.cos((-110 + i * 45) * deg) * x * 0.6 + x,
          Math.sin((-110 + i * 45) * deg) * y * 0.6 + y,
          x * 0.025,
          0 * deg,
          360 * deg
        );
        ctx.fillStyle = "#1bccff";
        ctx.fill();
        ctx.closePath();
      }
      for (let i = 0; i < 4; i++) {
        ctx.beginPath();
        ctx.arc(
          Math.cos((-105 + i * 45) * deg) * x * 0.6 + x,
          Math.sin((-105 + i * 45) * deg) * y * 0.6 + y,
          x * 0.025,
          0 * deg,
          360 * deg
        );
        ctx.fillStyle = "#1bccff";
        ctx.fill();
        ctx.closePath();
      }
    }
  }
};
</script>

<style scoped>
.canvas-box {
  width: 260px;
  height: 260px;
  margin-left: -20px;
  position: relative;
}
#canvas {
  width: 260px;
  height: 260px;
}
.size {
  font-size: 18px;
}
.day-posit {
  position: absolute;
  top: 40%;
  left: 45%;
}
b {
  font-size: 43px;
}
</style>
