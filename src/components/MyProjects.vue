<template>
  <section class="projects">
    <h3 class="projects__title">Реализованные проекты</h3>
    <carousel :items-to-show="1">
      <slide :key="1">
        <img src="../images/goldgarm.jpg" alt="GoldGarm" class="projects__image">
        <div class="projects__slide-container">
          <a href="https://goldgarm.ru/" class="projects__link">
            Gold Garm
          </a>
          <p class="projects__text">Одностраничный сайт-визитка для мебельной мастерской. Рассказывает о производстве,
            товарах и помогает потенциальным клиентам связаться с производителем.</p>
        </div>
      </slide>
      <slide :key="2">
        <h3 class="projects__title">проекты</h3>
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
    max-width: 1200px;
    padding: 0 120px;
    margin: 0 auto;
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

.projects__image {
  max-width: 400px;
  margin: 0 10px 10px 0;
  border-radius: 20px;
}

.projects__text {
  font-size: 20px;
  color: #f0f8ff;
  margin: 20px 0 0 0;
  cursor: default;
  transition: .5s;
  max-width: 700px;
}

@media screen and (max-width: 881px) {
  .projects {
    margin: 0 30px 0 30px;
    padding: 20px;

    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

@media screen and (max-width: 581px) {
  .projects {
    margin: 0 10px 0 10px;
  }
}

@media screen and (max-width: 441px) {
  .projects {
    margin: 0 5px;
    padding: 12px 5px;
  }

  .projects__title {
    font-size: 20px;
  }
}
</style>