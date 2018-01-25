<template>
  <div>
      <canvas id='canvas' ></canvas>
  </div>
</template>
<script>
export default {
  mounted:function(){
      this.draw();
  },
  methods:{
        draw(){
            var canvas = document.getElementById("canvas");
            canvas.width = innerWidth;
            canvas.height = innerHeight;
            var ctx = canvas.getContext("2d");
            ctx.beginPath();
            // ctx.fillRect(50,50,100,100);
            
            ctx.arc(100,100,50,Math.PI/180*0,Math.PI/180*360,false);
            ctx.fill();
            var x = Math.random()*innerWidth;
            var y = Math.random()*innerHeight;
            var dx = Math.random()*5;
            var dy = Math.random()*5;
            var radius = Math.random()*40;
            (function animate() {
                requestAnimationFrame(animate);
                //在同一个坐标无限循环画一个圆
                //重新定义开始坐标，试着注释掉这一行看看效果有何不同
                ctx.clearRect(0,0,innerWidth,innerHeight);
                ctx.beginPath();
                ctx.arc(x,y,40,0,Math.PI*2,false);
                ctx.stroke();
                if (x+radius>innerWidth || x-radius<0) {
                    dx = -dx;
                }
                if (y+radius>innerHeight || y-radius<0) {
                    dy = -dy;
                }
                console.log(x+radius,y+radius,dx,dy);
                //动态修改坐标
                x += dx;
                y += dy;
            })();
            // ctx.stroke();
        }
  }
}
</script>
<style scoped>
#canvas{
    border:1px solid;
}
</style>
