<template>
  <main ref='vantaRef' class="main">
    <section class="main__header">
      <div>
        <h1 class="main__title">KOCHETKOV</h1>
        <hr class="main__line" />
        <p class="main__subtitle">Студия разработки сайтов Дмитрия&nbsp;Кочеткова</p>
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
      <p class="main__text">Меня зовут Дмитрий Кочетков. Я веб-разработчик, который получил свои навыки, обучаясь в
        Яндексе. Чтобы
        процесс заказа сайта был удобным и понятным, я сделал для вас конфигуратор. В нём вы сможете выбрать нужные опции,
        узнать предварительную стоимость, а затем связаться со мной и получить сайт, разработанный по самым современным
        технологиям.</p>
    </section>
    <ConfiguratorModule></ConfiguratorModule>
    <MyProjects></MyProjects>
    <div class="main__contacts main__contacts-mobile">
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
      <p class="main__copy-message main__copy-message-mobile" v-bind:class="{ active: isHidden }">Скопировано</p>
    </div>
  </main>
</template>

<script>
import * as THREE from "three";
import HALO from 'vanta/dist/vanta.halo.min';
import ConfiguratorModule from './ConfiguratorModule.vue';
import MyProjects from './MyProjects.vue';
// Make sure window.THREE is defined, e.g. by including three.min.js in the document head using a <script> tag

export default {
  name: 'MainPage',
  components: {
    ConfiguratorModule,
    MyProjects
  },
  data() {
    return {
      isHidden: false,
    }
  },
  mounted() {
    const screenHeight = window.screen.height;
    console.log(screenHeight);
    // const screenHeight = window.screen.availHeight;
    // const screenHeight = document.documentElement.scrollHeight;

    const screenWidth = window.screen.width;

    let xOffset = 0.275;
    let yOffset = 0.275;
    // let size = 2.75;
    let size = 1.6;
    let speed = .8;
    let amplitudeFactor = .8;

    if (screenWidth < 881) {
      xOffset = 0.25;
      yOffset = -0.15;
      size = .9;
      speed = .5;
    } else if (screenWidth < 441) {
      xOffset = .5;
      yOffset = -.5;
      size = .1;
      speed = .1;
      amplitudeFactor = 1;
    }

    this.vantaEffect = HALO({
      el: this.$refs.vantaRef,
      THREE: THREE,
      backgroundColor: 0x000b24,
      amplitudeFactor: amplitudeFactor,
      xOffset: xOffset,
      yOffset: yOffset,
      size: size,
      speed: speed,
      // scaleMobile: window.devicePixelRatio,
      // scale: window.devicePixelRatio,
      // scaleMobile: 27,
      scaleMobile: 46,
      scale: 0.5,
      minHeight: 1550.00,
      // minHeight: screenHeight,
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
  letter-spacing: -2px;
}

.main__line {
  margin-left: 8px;
}

.main__subtitle {
  font-size: 19px;
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

.main__contacts-mobile {
  display: none;
  align-items: center;
  min-height: 120px;
  margin: 20px 5px 10px 5px;
  padding: 12px;
  padding-top: 40px;

  background-color: rgba(0, 2, 26, 0.45);
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #0f1329;
  transition: 1s;

  border-radius: 20px;
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

.main__copy-message-mobile {
  margin: 0 0 0 150px;
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

@media screen and (max-width: 881px) {
  .main__header {
    width: 100%;
    max-width: fit-content;
    padding: 50px 70px 0 70px;
    margin: 0 auto;
    align-self: flex-start;

    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .main__contacts {
    display: none;
  }

  .main__contacts-mobile {
    display: flex;
  }

  .main__navigation {
    margin: 50px 30px 30px 30px;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

}

@media screen and (max-width: 581px) {
  .main__header {
    padding: 40px 10px 0 10px;
  }

  .main__navigation {
    margin: 40px 10px 10px 10px;
  }
}

@media screen and (max-width: 441px) {
  .main__header {
    padding: 20px 5px 0 5px;
  }

  .main__title {
    font-size: 48px;
  }

  .main__navigation {
    margin: 30px 5px 10px 5px;
    padding: 12px;
  }

  .main__mini-title {
    font-size: 20px;
  }

  .main__text {
    font-size: 16px;
    margin-top: 15px;
    text-align: justify;
  }
}
</style>
