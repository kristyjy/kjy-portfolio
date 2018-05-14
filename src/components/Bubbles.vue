<template>
  <canvas width="1080" height="800"></canvas>
</template>

<script>
export default {
  name: 'Masthead',
  data() {
    return {
      particles: [],
      tick: 0,
      colors: [
        '255, 86, 124',
        '153, 225, 217',
        '255, 255, 255'
      ]
    }
  },
  methods: {
    loop() {
      window.requestAnimationFrame(this.loop); 
      this.createParticles(); 
      this.updateParticles();
      this.drawParticles(); 
      this.tick++;
    },
    updateParticles() {
      let height = this.$el.height;
      this.particles = this.particles.map(function(p) {
        p.y += p.speed; 
        if(p.y > height) { 
          p.y = 0;
          p.x = Math.random()*window.innerWidth;
        }
        return p;
      })
    },
    createParticles() { 
      if(this.tick % 10 == 0 && this.particles.length < 50) {
        this.particles.push({ 
          x: Math.random()*this.$el.width, 
          y: 0,
          speed: 1+Math.random()*1.5,
          radius: 5+Math.random()*10,
          color: this.getRandomColor(), 
        });
      }
    },
    drawParticles() { 
      let c = this.$el.getContext('2d');
      c.clearRect(0, 0, window.innerWidth, window.innerHeight);
      c.fillStyle = "transparent";
      c.fillRect(0, 0, window.innerWidth, window.innerHeight);

      this.particles.map(function(p) {
        c.beginPath();
        c.arc(p.x, p.y, p.radius, 0, Math.PI*2);
        c.closePath(); 
        c.fillStyle = p.color; 
        c.fill();
      });
    },
    getRandomColor() {
      return 'rgba(' + this.colors[Math.floor(this.getRandomNum(0,3))] + ',' + this.getRandomNum(.2, .8) + ')'
    },
    getRandomNum(min, max) {
      return Math.random() * (max - min) + min;
    },
    onResize() {
      this.$el.width = window.innerWidth;
      this.$el.height = window.innerHeight;
    }
  },
  mounted() {
    window.requestAnimationFrame(this.loop);
    this.onResize();
    window.addEventListener('resize', this.onResize, false);
  }
}
</script>

<style scoped>
canvas {
  display: block;
}
</style>
