<template>
  <main ref='vantaRef' class="main">
    <div class="main__header-block">
      <h1 class="main__title">DNKWORX</h1>
      <hr class="main__line"/>
      <p class="main__subtitle">Студия разработки сайтов Дмитрия Кочеткова</p>
    </div>
  </main>
</template>

<script>
import * as THREE from "three";
import HALO from 'vanta/dist/vanta.halo.min'
// Make sure window.THREE is defined, e.g. by including three.min.js in the document head using a <script> tag

export default {
  mounted() {
    this.vantaEffect = HALO({
      el: this.$refs.vantaRef,
      THREE: THREE,
      backgroundColor: 0x000b24,
      amplitudeFactor: 0.8,
      xOffset: 0.275,
      yOffset: 0.275,
      size: 1.75,
      speed: .8,
      // scaleMobile: window.devicePixelRatio,
      // scale: window.devicePixelRatio,
      scaleMobile: 1,
      scale: 0.5,
      minHeight: 900.00,
    })
  },
  beforeUnmount() {
    if (this.vantaEffect) {
      this.vantaEffect.destroy()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.main {
  display: flex;
  flex-direction: column;
}

.main__header-block {
  padding: 90px 0 0 70px;
  align-self: flex-start;
}

.main__title {
  font-size: 72px;
  color: #f0f8ff;
}

.main__line {
  margin-left: 8px;
}

.main__subtitle {
  font-size: 17px;
  color: #f0f8ff;
  margin-top: 10px;
  margin-left: 6px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}
</style>
