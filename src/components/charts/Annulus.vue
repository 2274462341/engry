<template>
  <div class="canvas-boxing">
    <p>单位/天</p>
    <canvas id="canvasdiv"></canvas>
    <div class="title">平均接电时间(高压)</div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      countList: [
        {
          title: "平均接电时间",
          totalTime: 10000,
          time: 2859,
          color: "#ff9486",
          dottedColor: "#70f098"
        },
        {
          title: "装表接电时间",
          totalTime: 8000,
          time: 3166,
          color: "#ede066",
          dottedColor: "#70f098"
        },
        {
          title: "竣工验收时间",
          totalTime: 8000,
          time: 3946,
          color: "#b9fb97",
          dottedColor: "#70f098"
        },
        {
          title: "中期检查时间",
          totalTime: 12000,
          time: 6681,
          color: "#67ef9c",
          dottedColor: "#70f098"
        },
        {
          title: "设计审查时间",
          totalTime: 12000,
          time: 7923,
          color: "#2ecce9",
          dottedColor: "#70f098"
        },
        {
          title: "供电方案答复时间",
          totalTime: 12000,
          time: 9215,
          color: "#4788fe",
          dottedColor: "#70f098"
        }
      ]
    };
  },
  mounted() {
    this.initCanvas(this.countList, {
      spacing: 30, //每一个圆的间隔
      radius: 40, //第一个圆的半径
      lineWidth: 16, //每个圆的宽度
      within: 21, //最外面的圆的身上的内刻线 长
      aside: 7, //最外面的圆的身上的外刻线 长
      withinx: 7, //最外面的圆的身上的内刻线 短
      TextStart: 2, //弧度上的文字开始间隔
      TextEnd: 10.5 //弧度上的文字每一个间隔
    });
  },
  methods: {
    initCanvas(list, obj) {
      let canvas = document.getElementById("canvasdiv");
      let ctx = canvas.getContext("2d");
      let winW = canvas.parentNode.offsetWidth;
      let winH = canvas.parentNode.offsetHeight;
      let deg = Math.PI / 180;
      canvas.width = winW;
      canvas.height = winH;

      let x = winW / 2;
      let y = winH / 2;

      const dragArc = (x, y, r, s, e, flag) => {
        ctx.arc(x, y, r, s * deg, e * deg, flag);
      };

      list.forEach((item, index) => {
        let i = 0;
        while (i < 360) {
          ctx.beginPath();
          dragArc(x, y, obj.radius + index * obj.spacing, i, i + 1);
          ctx.lineWidth = 0.5;
          ctx.strokeStyle = item.dottedColor;
          ctx.stroke();
          ctx.closePath();
          i += 10 - index;
        }
        ctx.beginPath();
        ctx.lineWidth = obj.lineWidth;
        dragArc(
          x,
          y,
          obj.radius + index * obj.spacing,
          -90,
          (item.time / item.totalTime) * 360 - 90
        );
        ctx.lineCap = "round";
        ctx.strokeStyle = item.color;
        ctx.stroke();

        ctx.closePath();
        ctx.beginPath();
        ctx.fillStyle = "#fff";
        ctx.font = "13px Georgia";
        ctx.textAlign = "right";
        ctx.textBaseline = "middle";
        ctx.fillText(item.title, x - 20, y - obj.radius - index * obj.spacing);
        ctx.fill();
        ctx.closePath();

        function drawCircularText(string, startAngle, endAngle, index) {
          var radius = obj.radius + index * obj.spacing; // 圆的半径
          var angleDecrement = (startAngle - endAngle) / (string.length - 1); // 每个字母占的弧度
          var angle = startAngle; //
          var ind = 0;
          var character;

          // if (index === 1) {
          //     angle = angle
          // }

          ctx.save();
          ctx.lineWidth = 0.5;
          ctx.fillStyle = "#fff";
          ctx.strokeStyle = "#fff";
          ctx.font = "13px Georgia";

          while (ind < string.length) {
            character = string.charAt(ind);
            ctx.save();
            ctx.beginPath();
            ctx.translate(
              x + Math.cos((Math.PI / 180) * angle) * radius,
              y + Math.sin((Math.PI / 180) * angle) * radius
            );
            ctx.rotate((Math.PI / 180) * (angle - 90)); // Math.PI/2为旋转90度  Math.PI/180*X为旋转多少度
            ctx.fillText(character, 0, 0);
            ctx.strokeText(character, 0, 0);
            angle -= angleDecrement;
            ind++;
            ctx.restore();
          }
          ctx.restore();
        }
        ctx.textAlign = "center";
        ctx.textBaseLine = "middle";
        console.log((item.time / item.totalTime) * 360 - 20 + index * 10);
        let str = Array.reverse(item.time.toString().split("")).join("");
        drawCircularText(
          str,
          (item.time / item.totalTime) * 360 - 70 - index * obj.TextStart,
          (item.time / item.totalTime) * 360 - 20 - index * obj.TextEnd,
          index
        );
      });
      ctx.beginPath();
      dragArc(x, y, obj.radius + obj.spacing * list.length, 0, 360);
      ctx.lineWidth = 0.5;
      ctx.strokeStyle = "#7fac81";
      ctx.stroke();
      ctx.closePath();

      let num = -90;
      let r = obj.radius + obj.spacing * list.length;

      while (num < 270) {
        ctx.beginPath();
        if (Math.abs(num) % 30 === 0) {
          ctx.moveTo(
            Math.cos(num * deg) * (r - obj.within) + x,
            Math.sin(num * deg) * (r - obj.within) + y
          );
          ctx.lineTo(
            Math.cos(num * deg) * (r + obj.aside) + x,
            Math.sin(num * deg) * (r + obj.aside) + y
          );
          ctx.lineWidth = 1;
          ctx.strokeStyle = "#8ce15f";
        } else {
          ctx.moveTo(Math.cos(num * deg) * r + x, Math.sin(num * deg) * r + y);
          ctx.lineTo(
            Math.cos(num * deg) * (r - obj.withinx) + x,
            Math.sin(num * deg) * (r - obj.withinx) + y
          );
          ctx.lineWidth = 0.5;
          ctx.strokeStyle = "#8ce15f";
        }

        ctx.stroke();
        ctx.closePath();
        num += 10;
      }
    }
  }
};
</script>

<style scoped>
.canvas-boxing {
  width: 480px;
  height: 480px;
  margin: 150px auto;
}
.canvas-boxing > p {
  text-align: right;
  word-spacing: 10;
  letter-spacing: 6px;
}
.title{
  font-size: 18px;
  margin-top:125px;
}
</style>
