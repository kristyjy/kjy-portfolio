<template>
  <section>
    <h2>My Skills</h2>
    <SkillChart />
  </section>
</template>

<script>
import SkillChart from './SkillChart.vue';

export default {
  name: 'Skills',
  components: {
    SkillChart
  }
}
</script>

<style scoped>
section {
  width: 100%;
  height: 100vh;
  position: relative;
}

section:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 30vh 0 0 100vw;
  border-color: transparent transparent transparent #333;
}

h2 {
  position: absolute;
  bottom: 100%;
  left: 0;
  width: 100%;
  text-align: center;
  font-size: 1.8rem;
}

@media (min-width: 768px) {
  h2 {
    font-size: 2.3rem;
  }
}

@media (min-width: 1100px) {
  h2 {
    font-size: 3rem;
  }
}
</style>