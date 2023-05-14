<template>
  <section class="configuration">
    <h3 class="configuration__title">Каким будет ваш новый&nbsp;сайт?</h3>
    <div class="configuration__card-box">
      <!-- Обертка для карточек -->
      <div class="configuration__card">
        <p class="configuration__text">Количество страниц на сайте</p>
        <form class="configuration__form-block">
          <div class="configuration__radio-row">
            <input id="1" type="radio" name="r" value="15000.0000000001" v-model="mainPrice" checked>
            <label class="configuration__label" for="1">Пока не знаю</label>
          </div>
          <div class="configuration__radio-row">
            <input id="2" type="radio" name="r" value="15000.000000001" v-model="mainPrice">
            <label class="configuration__label" for="2">Одностраничный</label>
          </div>
          <div class="configuration__radio-row">
            <input id="3" type="radio" name="r" value="30000" v-model="mainPrice">
            <label class="configuration__label" for="3">До 5 страниц</label>
          </div>
          <div class="configuration__radio-row">
            <input id="4" type="radio" name="r" value="45000" v-model="mainPrice">
            <label class="configuration__label" for="4">Более 5 страниц</label>
          </div>
        </form>
        <p class="configuration__text">Количество блоков на странице</p>
        <form class="configuration__form-block">
          <div class="configuration__radio-row">
            <input id="5" type="radio" name="r" value="1" v-model="multiplierDiv" checked>
            <label class="configuration__label" for="5">Пока не знаю</label>
          </div>
          <div class="configuration__radio-row">
            <input id="6" type="radio" name="r" value="1.000000001" v-model="multiplierDiv">
            <label class="configuration__label" for="6">До 3 блоков</label>
          </div>
          <div class="configuration__radio-row">
            <input id="7" type="radio" name="r" value="1.25" v-model="multiplierDiv">
            <label class="configuration__label" for="7">4 - 6 блоков</label>
          </div>
          <div class="configuration__radio-row">
            <input id="8" type="radio" name="r" value="1.5" v-model="multiplierDiv">
            <label class="configuration__label" for="8">Более 6 блоков</label>
          </div>
        </form>
      </div>
      <div class="configuration__card">
        <p class="configuration__text">Статический или динамический сайт</p>
        <form class="configuration__form-block">
          <div class="configuration__radio-row">
            <input id="9" type="radio" name="r" value="1" v-model="multiplierStaticOrDynamic" checked>
            <label class="configuration__label" for="9">Пока не знаю</label>
          </div>
          <div class="configuration__radio-row">
            <input id="10" type="radio" name="r" value="1.000000001" v-model="multiplierStaticOrDynamic">
            <label class="configuration__label" for="10">Статический</label>
          </div>
          <div class="configuration__radio-row">
            <input id="11" type="radio" name="r" value="1.2" v-model="multiplierStaticOrDynamic">
            <label class="configuration__label" for="11">Частично изменяемый</label>
          </div>
          <div class="configuration__radio-row">
            <input id="12" type="radio" name="r" value="2.2" v-model="multiplierStaticOrDynamic">
            <label class="configuration__label" for="12">Динамический</label>
          </div>
        </form>
        <p class="configuration__text">Изменяемая тема на сайте</p>
        <form class="configuration__form-block">
          <div class="configuration__radio-row">
            <input id="13" type="radio" name="r" value="0" v-model="priceTheme" checked>
            <label class="configuration__label" for="13">Пока не знаю</label>
          </div>
          <div class="configuration__radio-row">
            <input id="14" type="radio" name="r" value="0.000000001" v-model="priceTheme">
            <label class="configuration__label" for="14">Не нужна</label>
          </div>
          <div class="configuration__radio-row">
            <input id="15" type="radio" name="r" value="5000" v-model="priceTheme">
            <label class="configuration__label" for="15">Нужна</label>
          </div>
        </form>
      </div>
      <div class="configuration__card">
        <p class="configuration__text">Дизайн - макет сайта</p>
        <form class="configuration__form-block">
          <div class="configuration__radio-row">
            <input id="16" type="radio" name="r" value="1" v-model="multiplierDesign" checked>
            <label class="configuration__label" for="16">Уже есть</label>
          </div>
          <div class="configuration__radio-row">
            <input id="18" type="radio" name="r" value="1.2" v-model="multiplierDesign">
            <label class="configuration__label" for="18">Нужно соблюсти лишь общую стилистику</label>
          </div>
          <div class="configuration__radio-row">
            <input id="19" type="radio" name="r" value="1.5" v-model="multiplierDesign">
            <label class="configuration__label" for="19">Нужна проработка с дизайнером</label>
          </div>
        </form>

        <hr class="configuration__line" />
        <!-- <div class="configuration__price-block"> -->
          <p class="configuration__text">Предварительная стоимость:</p>
          <p class="configuration__text">
            От
            <span class="configuration__text" v-show="this.fullPrice">{{ this.fullPrice }}</span>
            &#x20bd;
          </p>
          <!-- <p class="configuration__text">Скопировать настройки для обсуждения заказа</p> -->
          <div class="configuration__contacts-block" v-bind:class="{ active: isActive }">
        <a class="configuration__contact" @click.prevent="copySettings" title="Скопировать"><img class="configuration__icon"
            src="../images/icon-copy.svg" alt="Нажмите, чтобы скопировать"></a>
        <a class="configuration__contact" @click.prevent="copySettings" ref="settings" value="settings"
          title="Скопировать">Скопировать выбранные данные для обсуждения заказа</a>
      </div>
        <!-- </div> -->

      </div>
    </div>
  </section>
</template>

<script>

export default {
  name: 'ConfiguratorModule',
  data() {
    return {
      isActive: false,
      settings: '',
      mainPrice: 15000,
      multiplierDiv: 1,
      multiplierStaticOrDynamic: 1,
      priceTheme: 0,
      multiplierDesign: 1,
      fullPrice: 15000,
    }
  },
  methods: {
    calculatePrice() {
      let price = 0;
      price = this.mainPrice * this.multiplierDiv * this.multiplierStaticOrDynamic * this.multiplierDesign + +this.priceTheme;
      this.fullPrice = Math.trunc(price);

      let priceMessage = 'Одностраничный или более, ';
      let divMessage = '';
      let staticOrDynamicMessage = '';
      let designMessage = '';
      let themeMessage = 'дизайн уже разработан.';

      if (this.mainPrice === "15000.0000000001") {
        priceMessage = 'Одностраничный или более, ';
      } else if (this.mainPrice === "15000.000000001") {
        priceMessage = 'Одностраничный, ';
      } else if (this.mainPrice === "30000") {
        priceMessage = 'До 5 страниц, ';
      } else if (this.mainPrice === "45000") {
        priceMessage = 'Более 5 страниц, ';
      }

      if (this.multiplierDiv === "1") {
        divMessage = '';
      } else if (this.multiplierDiv === "1.000000001") {
        divMessage = 'до 3 блоков на странице, ';
      } else if (this.multiplierDiv === "1.25") {
        divMessage = '4-6 блоков на странице, ';
      } else if (this.multiplierDiv === "1.5") {
        divMessage = 'более 6 блоков на странице, ';
      }

      if (this.multiplierStaticOrDynamic === "1") {
        staticOrDynamicMessage = '';
      } else if (this.multiplierStaticOrDynamic === "1.000000001") {
        staticOrDynamicMessage = 'статический, ';
      } else if (this.multiplierStaticOrDynamic === "1.2") {
        staticOrDynamicMessage = 'частично изменяемый, ';
      } else if (this.multiplierStaticOrDynamic === "2.2") {
        staticOrDynamicMessage = 'динамический, ';
      }

      if (this.multiplierDesign === "1") {
        designMessage = 'дизайн уже разработан.';
      } else if (this.multiplierDesign === "1.2") {
        designMessage = 'в плане дизайна нужно соблюсти лишь общую стилистику.';
      } else if (this.multiplierDesign === "1.5") {
        designMessage = 'нужна проработка с дизайнером.';
      }

      if (this.priceTheme === "0") {
        themeMessage = '';
      } else if (this.priceTheme === "0.000000001") {
        themeMessage = 'изменяемая тема сайта не нужна, ';
      } else if (this.priceTheme === "5000") {
        themeMessage = 'нужна изменяемая тема сайта, ';
      }

      this.settings = priceMessage + divMessage + staticOrDynamicMessage + themeMessage + designMessage;

      // debugger; // eslint-disable-line no-debugger
    },
    copySettings() {
      this.calculatePrice();
      window.navigator.clipboard.writeText(this.settings);

      this.isActive = !this.isActive;
      setTimeout(() => {
        this.isActive = !this.isActive;
      }, 1000)
    },
  },
  watch: {
    mainPrice: function () {
      this.calculatePrice();
    },
    multiplierDiv: function () {
      this.calculatePrice();
    },
    multiplierStaticOrDynamic: function () {
      this.calculatePrice();
    },
    priceTheme: function () {
      this.calculatePrice();
    },
    multiplierDesign: function () {
      this.calculatePrice();
    },
  },
}
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.configuration {
  max-width: 1920px;
  min-height: 100px;

  background-color: rgba(0, 2, 26, 0.45);
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #0f1329;
  transition: 1s;

  border-radius: 20px;

  margin: 40px 70px 0 70px;
  padding: 20px;
}

.configuration:hover {
  box-shadow: 0 0 19px #222222;
  transition: 1s;
}

.configuration__title {
  font-size: 28px;
  color: #f0f8ff;
  /* text-decoration: underline; */
  max-width: fit-content;
  cursor: default;
}

.configuration__text {
  font-size: 20px;
  color: #f0f8ff;
  // text-align: left;
  margin: 20px 0 0 0;
  cursor: default;

  // align-self: flex-start;
  transition: .5s;
  width: fit-content;
}

.configuration__card-box {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin: 10px 0 0 0;
}

.configuration__card {
  min-width: 200px;
  min-height: 400px;
  width: 100%;
  // border: 2px solid rgba(109, 7, 129, 0.151);
  border-radius: 10px;
  margin: 10px;
  padding: 12px;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #0f1329;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.configuration__radio-row {
  display: flex;
  flex-direction: row;
  gap: 10px;
  margin: 10px 0 0 0;
}

.configuration__line {
  width: 80%;
  margin-top: 20px;
}

.configuration__price-block {
  margin: 0 0 20px 0;
  height: 100%;
}

.configuration__form-block {
  --text: #f0f8ff;
  --radio: #7C96B2;
  --radio-checked: #b900cad7;
  --radio-size: 20px;
  // width: 80%;
  height: 100%;
  color: var(--text);
  box-shadow: 0 10px 30px rgba(#414856, 0.05);
  min-width: 220px;
  padding: 0 20px 0 0;

  label {
    font-size: 17px;
    text-align: left;
    cursor: pointer;
  }

  input[type="radio"] {
    -webkit-appearance: none;
    -moz-appearance: none;
    position: relative;
    height: 20px;
    width: 20px;
    outline: none;
    margin: 0;
    cursor: pointer;
    border: 2px solid var(--radio);
    background: transparent;
    border-radius: 50%;
    display: grid;
    justify-self: end;
    justify-items: center;
    align-items: center;
    overflow: hidden;
    transition: border .5s ease;

    &::before,
    &::after {
      content: "";
      display: flex;
      justify-self: center;
      border-radius: 50%;
    }

    &::before {
      position: absolute;
      width: 20px;
      height: 20px;
      background: var(--background);
      z-index: 1;
      opacity: var(--opacity, 1);
    }

    &::after {
      position: relative;
      width: calc(100% /2);
      height: calc(100% /2);
      background: var(--radio-checked);
      top: var(--y, 100%);
      transition: top .5s cubic-bezier(0.48, 1.97, 0.5, 0.63);
    }

    &:checked {
      --radio: var(--radio-checked);

      &::after {
        --y: 0%;
        animation: stretch-animate .3s ease-out .17s;
      }

      &::before {
        --opacity: 0;
      }

      ~input[type="radio"] {
        &::after {
          --y: -100%;
        }
      }
    }

    &:not(:checked) {
      &::before {
        --opacity: 1;
        transition: opacity 0s linear .5s;
      }
    }
  }
}

.configuration__form-block .configuration__label {
  max-width: 290px;
}

.configuration__contacts-block {
  display: flex;
  flex-direction: row;
  align-items: center;
  max-width: 358px;

  border: 2px solid #b900ca5d;
  border-radius: 20px;
  padding: 10px;
  
  transition: border .5s ease;
}

.configuration__contacts-block:hover {
  opacity: .8;
  transition: opacity .5s ease;
}

.configuration__contact {
  font-size: 18px;
  color: #f0f8ff;
  text-decoration: none;
  cursor: pointer;
}

.configuration__icon {
  width: 40px;
  height: 40px;
  margin: 0 10px 0 0;
}

.configuration__icon:hover {
  filter: blur(50%);
}

.active {
  border: 2px solid #f6a3ff5d;
  transition: border .5s ease;
}

@keyframes stretch-animate {
  0% {
    transform: scale(1, 1)
  }

  28% {
    transform: scale(1.15, .85)
  }

  50% {
    transform: scale(.9, 1.1)
  }

  100% {
    transform: scale(1, 1)
  }
}

@media screen and (max-width: 1279px) {
  .configuration__form-block .configuration__label {
  font-size: 16px;
  max-width: 150px;
}

.configuration__card {
  padding: 12px;
}
}

@media screen and (max-width: 881px) {
  .configuration {
  margin: 0 30px 0 30px;
  padding: 20px;

  display: flex;
  flex-direction: column;
  align-items: center;
}

.configuration__text {
  font-size: 24px;
}

.configuration__form-block .configuration__label {
  font-size: 22px;
}

.configuration__card-box {
  flex-direction: column;
  align-items: center;
  margin: 10px 0 0 0;
  width: 100%;
}

.configuration__form-block  {
  padding: 0 0 10px 0;
}

}

@media screen and (max-width: 681px) {
  .configuration__text {
  font-size: 22px;
}

.configuration__form-block .configuration__label {
  font-size: 20px;
}
}

@media screen and (max-width: 581px) {
  .configuration {
    margin: 0 10px 0 10px;
}
  .configuration__form-block  {
  max-width: 320px;
}
}

@media screen and (max-width: 441px) {
  .configuration {
    margin: 0 5px;
    padding: 12px 5px;
}

  .configuration__title {
  font-size: 20px;
}

.configuration__text {
  font-size: 16px;
  padding: 0 5px;
}

.configuration__form-block .configuration__label {
  font-size: 16px;
  max-width: 150px;
}

.configuration__form-block {
  padding: 0 5px 0 5px;
}

.configuration__card {
  min-height: 350px;
  padding-bottom: 15px;
}

.configuration__icon {
  display: none;
}
}
</style>
