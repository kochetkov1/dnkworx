<template>
  <section class="projects">
    <h3 class="projects__title">Реализованные проекты</h3>
    <carousel :items-to-show="1">
      <slide :key="1">
        <div class="projects__image-container">
          <img src="../images/goldgarm.png" alt="GoldGarm" class="projects__image">
          <span class="projects__image-glare"></span>
        </div>
        <div class="projects__slide-container">
          <a href="https://goldgarm.ru/" class="projects__link" target="_blank">
            GOLD GARM
          </a>
          <p class="projects__text">GOLD GARM – это мастерская лофт мебели с философией свободы и практичности.
            Мы сделали одностраничный сайт-визитку, который рассказывает о идеологии, продуктах и производстве.
            Помогает найти отклик в сердцах потенциальных клиентов и дает им возможность напрямую связаться с
            производителем.</p>
        </div>
      </slide>
      <slide :key="2">
        <div class="projects__image-container">
          <img src="../images/russian-travel.png" alt="Путешествия по России" class="projects__image">
          <span class="projects__image-glare"></span>
        </div>
        <div class="projects__slide-container">
          <a href="https://kochetkov1.github.io/russian-travel/" class="projects__link" target="_blank">
            Путешествия по России
          </a>
          <p class="projects__text">По опросам ВЦИОМ, 95% россиян мечтают куда-нибудь поехать, но только 36% планируют
            провести отпуск в родной стране. Мол, чего мы тут, дома, не видели? На самом деле, Россия — это целая
            вселенная с ласковым морем юга, густыми лесами Саян и суровыми льдами плато Путорана. Мы выбрали и описали
            некоторые интересные места, достойные вашего отпуска.</p>
        </div>
      </slide>

      <template #addons>
        <navigation />
        <pagination />
      </template>
    </carousel>
  </section>
</template>

<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

export default {
  name: 'MyProjects',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
    }
  },
  methods: {

  }
}
</script>

<style>
.carousel {
  /* max-width: 1480px; */
  /* padding: 0 80px; */
  margin: 0 auto;
  width: 100%;
}

.carousel__slide {
  padding: 0 50px 0 50px;
}

.carousel__icon {
  fill: #f0f8ff;
}

.carousel__pagination-button::after {
  background-color: #f0f8ff67;
}

.carousel__pagination-button--active::after {
  background-color: #f0f8ff;
}

.carousel__pagination {
  padding: 0;
}
</style>
<style lang="scss" scoped>
.projects {
  max-width: 1920px;
  min-height: 100px;

  background-color: rgba(0, 2, 26, 0.45);
  backdrop-filter: blur(10px);
  box-shadow: 0 0 15px #0f1329;
  transition: 1s;

  border-radius: 20px;

  margin: 40px 70px 40px 70px;
  padding: 20px;
}

.projects:hover {
  box-shadow: 0 0 19px #222222;
  transition: 1s;
}

.projects__title {
  font-size: 28px;
  color: #f0f8ff;
  /* text-decoration: underline; */
  max-width: fit-content;
  cursor: default;
  margin: 0;
}

.projects__link {
  font-size: 28px;
  color: #f0f8ff;
  // text-decoration: none;
}

.projects__slide-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.projects__image-container {
  max-width: 800px;
  max-height: 400px;
  width: 100%;
  overflow: scroll;
  position: relative;
  overflow-x: hidden;
  border-radius: 10px;
  margin-right: 40px;
  box-shadow: 0 0 10px #222222;
}

.projects__image {
  max-width: 800px;
  width: 100%;
  margin: 0;
}

.projects__image-glare {
  position: absolute;
  top: 0;
  height: 100%;
  width: 150px;
  transform: skewX(40deg); // Наклон
  animation: flareAnimation;
  left: -150%;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.15));
  animation: flareAnimation 5s infinite linear; // Время и тип анимации можно менять
}

@keyframes flareAnimation {
  0% {
    left: -150%;
  }

  100% {
    left: 300%;
  }
}

.projects__text {
  font-size: 20px;
  color: #f0f8ff;
  margin: 20px 0 0 0;
  cursor: default;
  transition: .5s;
  max-width: 600px;
  text-align: justify;
}

@media screen and (max-width: 881px) {
  .projects {
    margin: 0 30px 0 30px;
    padding: 20px;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .carousel__slide {
    flex-direction: column;
  }

  .projects__image-container {
    margin: 0 0 40px 0;
  }
}

@media screen and (max-width: 581px) {
  .projects {
    margin: 10px 10px 0 10px;
  }
}

@media screen and (max-width: 441px) {
  .projects {
    margin: 10px 5px 0 5px;
    padding: 12px 5px;
  }

  .projects__title {
    font-size: 20px;
  }

  .projects__text {
    font-size: 16px;
  }

  .carousel__slide {
    padding: 0 35px 0 35px;
  }
}
</style>