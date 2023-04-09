<template>
  <section class="configuration">
    <h3 class="configuration__title">Каким будет ваш новый сайт?</h3>
    <div class="configuration__card-box">
      <!-- Обертка для карточек -->
      <div class="configuration__card">
        <p class="configuration__text">Количество страниц</p>
        <form>
          <div class="configuration__radio-row">
            <input id="01" type="radio" name="r" value="1" checked>
            <label for="01">Одностраничный</label>
          </div>
          <div class="configuration__radio-row">
            <input id="02" type="radio" name="r" value="2">
            <label for="02">До 5 страниц</label>
          </div>
          <div class="configuration__radio-row">
            <input id="03" type="radio" name="r" value="3">
            <label for="03">Более 5 страниц</label>
          </div>
        </form>
        <p class="configuration__text">Количество блоков на странице</p>
        <form>
          <div class="configuration__radio-row">
            <input id="04" type="radio" name="r" value="1" checked>
            <label for="04">До 3 блоков</label>
          </div>
          <div class="configuration__radio-row">
            <input id="05" type="radio" name="r" value="2">
            <label for="05">3 - 5 блоков</label>
          </div>
          <div class="configuration__radio-row">
            <input id="06" type="radio" name="r" value="3">
            <label for="06">Более 5 блоков</label>
          </div>
        </form>
      </div>
      <div class="configuration__card">
        <p class="configuration__text">Статический или динамический сайт</p>
        <form>
          <div class="configuration__radio-row">
            <input id="07" type="radio" name="r" value="1" checked>
            <label for="07">Статический</label>
          </div>
          <div class="configuration__radio-row">
            <input id="08" type="radio" name="r" value="2">
            <label for="08">Динамический</label>
          </div>
        </form>
        <p class="configuration__text">Переключаемая тема на сайте (тёмная / светлая)</p>
        <form>
          <div class="configuration__radio-row">
            <input id="09" type="radio" name="r" value="1" checked>
            <label for="09">Нужна</label>
          </div>
          <div class="configuration__radio-row">
            <input id="10" type="radio" name="r" value="2">
            <label for="10">Не нужна</label>
          </div>
        </form>
      </div>
      <div class="configuration__card"></div>
    </div>
  </section>
</template>

<script>

export default {
  data() {
    return {

    }
  },
  methods: {

  }
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
  font-size: 17px;
  color: #f0f8ff;
  text-align: left;
  margin-top: 20px;
  cursor: default;
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
  border: 2px solid rgba(109, 7, 129, 0.151);
  border-radius: 10px;
  margin: 10px;
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

form {
  --text: #f0f8ff;
  --radio: #7C96B2;
  --radio-checked: #b900cad7;
  --radio-size: 20px;
  background: var(--background);
  width: var(--width);
  height: var(--height);
  border-radius: var(--border-radius);
  color: var(--text);
  box-shadow: 0 10px 30px rgba(#414856, 0.05);

  label {
    cursor: pointer;
  }

  input[type="radio"] {
    -webkit-appearance: none;
    -moz-appearance: none;
    position: relative;
    height: var(--radio-size);
    width: var(--radio-size);
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
      width: 100%;
      height: 100%;
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


</style>
