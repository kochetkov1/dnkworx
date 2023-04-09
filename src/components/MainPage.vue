<template>
  <main ref='vantaRef' class="main">
    <section class="main__header">
      <div>
        <h1 class="main__title">DNKWORX</h1>
        <hr class="main__line" />
        <p class="main__subtitle">Студия разработки сайтов Дмитрия Кочеткова</p>
      </div>
      <div class="main__contacts">
        <div class="main__contacts-block">
          <a href="http://t.me/kochetkov111" class="main__contact" target="_blank"><img class="main__icon"
              src="../images/icon-telegram.svg" alt="Telegram" title="Перейти в Telegram"></a>
          <a href="http://t.me/kochetkov111" class="main__contact" target="_blank"
            title="Перейти в Telegram">kochetkov111</a>
        </div>
        <div class="main__contacts-block">
          <a class="main__contact" @click.prevent="copyToClipboard" title="Скопировать E-mail"><img class="main__icon"
              src="../images/icon-mail.svg" alt="Нажмите, чтобы скопировать"></a>
          <a class="main__contact" @click.prevent="copyToClipboard" ref="email" value="dnkworx@vk.com"
            title="Скопировать E-mail">dnkworx@vk.com</a>
        </div>
        <p class="main__copy-message" v-bind:class="{ active: isHidden }">Скопировано</p>
      </div>
    </section>
    <section class="main__navigation">
      <h3 class="main__mini-title">О студии и её основателе</h3>
      <p class="main__text">Меня зовут Дмитрий Кочетков. Я веб-разработчик, который получил свои навыки, обучаясь в Яндексе. Чтобы
        процесс заказа сайта был удобным и понятным, я сделал для вас конфигуратор. В нём вы сможете выбрать нужные опции,
        узнать предварительную стоимость, а затем связаться со мной и получить сайт, разработанный по самым современным
        технологиям.</p>
    </section>
    <ConfiguratorModule></ConfiguratorModule>
  </main>
</template>

<script>
import * as THREE from "three";
import HALO from 'vanta/dist/vanta.halo.min';
import ConfiguratorModule from './ConfiguratorModule.vue';
// Make sure window.THREE is defined, e.g. by including three.min.js in the document head using a <script> tag

export default {
  name: 'MainPage',
  components: {
    ConfiguratorModule
  },
  data() {
    return {
      isHidden: false,
    }
  },
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
      minHeight: 980.00,
    })
  },
  beforeUnmount() {
    if (this.vantaEffect) {
      this.vantaEffect.destroy()
    }
  },
  methods: {
    copyToClipboard() {
      window.navigator.clipboard.writeText(this.$refs.email.textContent);
      this.isHidden = !this.isHidden;
      setTimeout(() => {
        this.isHidden = !this.isHidden;
      }, 1000)
    },
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
  padding: 50px 0 0 70px;
  align-self: flex-start;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.main__title {
  font-size: 72px;
  color: #f0f8ff;
  cursor: default;
}

.main__line {
  margin-left: 8px;
}

.main__subtitle {
  font-size: 17px;
  color: #f0f8ff;
  margin-top: 10px;
  margin-left: 6px;
  cursor: default;
}

.main__contacts {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-right: 140px;
}

.main__contacts-block {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.main__contacts-block:hover {
  opacity: .8;
  transition: opacity .5s ease;
}

.main__contact {
  font-size: 28px;
  color: #f0f8ff;
  text-decoration: underline;
  cursor: pointer;
}

.main__icon {
  width: 50px;
  height: 50px;
  margin: 0 10px 0 0;
}

.main__icon:hover {
  filter: blur(50%);
}

.main__copy-message {
  font-size: 18px;
  color: #f0f8ff;
  margin: 0 0 0 175px;
  padding: 10px;
  opacity: 0;
  transition: opacity .5s ease;
  border: 2px solid #f0f8ff;
  border-radius: 0 20px 20px 20px;
}

.active {
  opacity: .8;
  transition: opacity .5s ease;
}

.main__navigation {
  max-width: 820px;
  min-height: 100px;

  background-color: rgba(0, 2, 26, 0.45);
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #0f1329;
  transition: 1s;

  border-radius: 20px;

  margin: 0 0 0 70px;
  padding: 20px;
}

.main__navigation:hover {
  box-shadow: 0 0 19px #222222;
  transition: 1s;
}

.main__mini-title {
  font-size: 28px;
  color: #f0f8ff;
  /* text-decoration: underline; */
  max-width: fit-content;
  cursor: default;
}
.main__text {
  font-size: 17px;
  color: #f0f8ff;
  text-align: left;
  margin-top: 20px;
  cursor: default;
}
</style>
