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
  padding-bottom: 20vh;
  position: relative;
  background-color: #eee;
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
  border-color: transparent transparent transparent var(--color1);
}

h2 {
  margin: 0 0 1rem;
  text-align: center;
  font-size: 2.5rem;
}

@media (min-width: 768px) {
  h2 {
    font-size: 3rem;
  }
}

@media (min-width: 1100px) {
  h2 {
    font-size: 4rem;
  }
}
</style>