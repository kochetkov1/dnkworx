<template>
  <main ref='vantaRef' class="main">
    <section class="main__header">
      <div>
        <h1 class="main__title">DNKWORX</h1>
        <hr class="main__line" />
        <p class="main__subtitle">Студия разработки сайтов Дмитрия Кочеткова</p>
      </div>
      <div class="main__contacts">
        <a href="http://t.me/kochetkov111" class="main__contact" target="_blank"><img class="main__telegram-icon" src="../images/icon-telegram.svg" alt="Telegram"></a>
        <!-- <p class="main__contact">kochetkov111</p> -->
        <a href="http://t.me/kochetkov111" class="main__contact" target="_blank">kochetkov111</a>
      </div>
    </section>
    <section class="main__navigation">
      <div class="wave1"></div>
      <div class="wave2"></div>
    </section>
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
      size: 2.75,
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

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

.main {
  display: flex;
  flex-direction: column;
}

.main__header {
  width: 100%;
  padding: 90px 0 0 70px;
  align-self: flex-start;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
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

.main__contacts {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-right: 140px;
}

.main__contact {
  font-size: 28px;
  color: #f0f8ff;
}

.main__telegram-icon {
  width: 50px;
  height: 50px;

  margin: 0 10px 0 0;
}

.main__navigation {
  max-width: 820px;
  min-height: 100px;

  background-color: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #353535;
  transition: 1s;

  border-radius: 10px;

  margin: 50px 0 0 70px;
}

.main__navigation:hover {
  box-shadow: 0 0 19px #444444;
  transition: 1s;
}

@keyframes wave {
  100% {
    transform: rotate(360deg);
  }
}
</style>
