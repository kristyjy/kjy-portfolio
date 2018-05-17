<template>
  <section>
    <h2>About Me</h2>
    <p>I am an experienced web developer specializing in front-end development. I build user-friendly, standards compliant web applications and websites. I'm well versed in cross-browser compatibility, front-end best practices, responsive design and performance optimization.</p>
    <div aria-hidden="true" class="circles"></div>
  </section>
</template>

<script>
export default {
  name: 'AboutMe'
}
</script>

<style scoped>
section {
  padding-bottom: 30vh;
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
  border-color: transparent transparent transparent #eee;
}

h2 {
  margin: 0 0 2rem;
  text-align: center;
  font-size: 2.5rem;
  color: var(--color1);
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

p {
  max-width: 40rem;
  line-height: 1.5;
  margin: 1rem auto;
  font-size: 1.4rem;
  text-align: center;
  max-width: 25rem;
}

@media (min-width: 768px) {
  p {
    font-size: 1.6rem;
    max-width: 30rem;
  }
}

@media (min-width: 1100px) {
  p {
    font-size: 1.8rem;
    max-width: 45rem;
  }
}

.circles {
  display: block;
  position: relative;
  margin: 2rem auto 0;
  width: 4rem;
  height: 4rem;
  border-radius: 4rem;
  background-color: var(--color2);
}

.circles:before {
  content: '';
  position: absolute;
  left: -1.2rem;
  top: 1.4rem;
  width: 3rem;
  height: 3rem;
  border-radius: 3rem;
  background-color: var(--color1);
  opacity: .5;
}

.circles:after {
  content: '';
  position: absolute;
  right: -.5rem;
  top: -.4rem;
  width: 2rem;
  height: 2rem;
  border-radius: 2rem;
  background-color: #666;
  opacity: .5;
}
</style>