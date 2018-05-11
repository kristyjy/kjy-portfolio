<template>
  <main class="masthead">
    <transition-group tag="div" name="text" class="text-container" appear>
      <h2 class="text greeting" key="greetings" >Greetings!</h2>
      <p class="text name" key="name" v-if="showName">I'm Kristy.</p>
      <p class="text tagline" key="tagline" v-if="showTagline">I bring designs to life.</p>
    </transition-group>
  </main>
</template>

<script>
export default {
  name: 'Masthead',
  data() {
    return {
      showName: false,
      showTagline: false
    }
  },
  mounted() {
    let t = this;
    let name = setTimeout(function(){
      t.showName = true;
      clearTimeout(name);
    }, 2000);
    let tag = setTimeout(function(){
      t.showTagline = true;
      clearTimeout(tag);
    }, 4000);
  }
}
</script>

<style scoped>
.masthead {
  width: 100%;
  height: 100vh;
  background-color: #333;
  padding: 10px 0;
  color: #fff;
  text-align: center;
  font-size: 1.5rem;
  position: relative;
}

.masthead:before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 50vw 15vh 0;
  border-color: transparent #fff transparent transparent;
}

.masthead:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 30vh 0 0 100vw;
  border-color: transparent transparent transparent #fff;
}

@media (min-width: 768px) {
  .masthead {
    font-size: 2.3rem;
  }
}

@media (min-width: 1100px) {
  .masthead {
    font-size: 3rem;
  }
}

.text-container {
  position: relative;
  top: 15vh;
  height: 55vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.greeting {
  font-size: 2.5em;
  margin: 0 0 2rem;
}

.name {
  margin: 1rem 0;
}

.tagline {
  font-size: 1.6em;
  font-family: 'Pacifico';
  margin: 1rem 0;
}

.text {
  transition: all 1s;
}

.text-enter, 
.text-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

.text-leave-active {
  position: absolute;
}
</style>
