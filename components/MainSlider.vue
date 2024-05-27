<template>
  <main class="main">
    <Loader v-if="slides.length === 0"></Loader>
    <Swiper class="slider" v-else :spaceBetween="30" :effect="'fade'" :pagination="pagination" :navigation="true"
      :speed="600" :parallax="true" :modules="modules">
      <SwiperSlide v-for="slide in slides" :key="slide.title + slide.id" class="slide">
        <img :src="slide.image" alt="{{slide.title}}" data-swiper-parallax="-300" />
        <div class="slide-descr container">
          <h2 data-swiper-parallax="-100">{{ slide.title }}</h2>
          <div class="descr-block descr-block-sub ">
            <div data-swiper-parallax="-300" class="descr-item" v-for="item in slide.description"
              :key="slide.description.id">
              <h3 data-swiper-parallax="-100" data-swiper-parallax-duration="500">{{ item.title }} </h3>
              <p>{{ item.description }}</p>
            </div>
          </div>
          <div class="descr-block" data-swiper-parallax="0">
            <a :href="slide.link" class="link__more">Read More</a>
            <a :href="slide.link" class="link__project">
              <span></span>
              View project
            </a>
          </div>
        </div>
      </SwiperSlide>
    </Swiper>
  </main>
</template>
<script>
import { ref, onBeforeMount, defineComponent, onUpdated, onMounted } from "vue";

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Pagination, Navigation, EffectFade, Parallax } from 'swiper';
import Loader from "./Loader.vue";
import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/navigation';
import 'swiper/css/effect-fade';

export default defineComponent({
  components: { SwiperSlide, Swiper, Loader },
  setup() {
    const slides = ref([]);
    const loadSlides = async () => {
      try {
        const response = await fetch(
          "https://664878da2bb946cf2fa0af05.mockapi.io/api/v1/menu"
        );
        const data = await response.json();
        slides.value = data;
        console.log(data);
      } catch (error) {
        console.log("Ошибка загрузки слайдов:", error);
      }
    };
    onBeforeMount(loadSlides);
    return {
      slides,
      loadSlides,
      pagination: {
        clickable: true,
        type: 'custom',
        renderCustom: function (swiper, current, total) {
          return `<span>${current > 10 ? current : '0' + current}</span><span class="pagin"></span><span>${total > 10 ? total : '0' + total}</span>`;
        },
      },
      modules: [Pagination, Navigation, EffectFade, Parallax]
    };
  },
});
</script>
<style lang="scss">
.main {
  position: relative;
  top: -100px;
  min-height: 100vh;
}

.slider {
  width: 100%;
  height: 100%;

  img {
    object-fit: cover;
    position: absolute;
    bottom: 0;
    // top: 100px;
    // margin-top: 100px;
  }

  .slide {
    background: #f3f3f3;
  }

  .swiper-pagination {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .swiper-button-next,
  .swiper-button-prev {
    top: unset;
    bottom: -5px;
    cursor: pointer;

    &::after {
      content: '';
      width: 10px;
      height: 10px;
      border-top: 2px solid #444444;
      border-right: 2px solid #444444;
    }
  }

  .swiper-button-next {
    right: calc(50% - 150px);

    &::after {
      transform: rotate(45deg);
    }
  }

  .swiper-button-prev {
    left: calc(50% - 150px);

    &::after {
      transform: rotate(-135deg);
    }

  }

  .pagin {
    display: inline-block;
    width: 180px;
    height: 1px;
    background-color: #425A20;
    margin: 0 10px;
  }

  .slide-descr {
    display: flex;
    flex-direction: column;
    padding-top: 250px;
    padding-bottom: 100px;
    min-height: 100vh;
    align-items: flex-start;
    justify-content: center;

    h2 {
      font-family: "PlayfairDisplay", serif;
      font-size: 96px;
      line-height: 100%;
      font-weight: 700;
      color: #425A20;
      margin-bottom: 40px;
    }

    .descr-block {
      display: flex;
      align-items: center;

      &-sub {
        margin-bottom: 40px;
      }

      .descr-item {
        max-width: 285px;

        &:first-child {
          margin-right: 58px;
        }

        h3 {
          font-size: 18px;
          font-weight: 400;
          color: #425A20;
          margin-bottom: 16px;
        }

        p {
          font-family: "FuturabookC", sans-serif;
          color: #44444490;
          font-size: 14px;
          line-height: 18px;
        }
      }

      .link__more {
        position: relative;
        min-width: 200px;
        padding: 20px 40px;
        background: #597D4E;
        font-size: 18px;
        color: #fff;
        text-align: center;
        border-radius: 5px;
        transition: all 0.3s ease-in-out;
        margin-right: 40px;

        &::after {
          content: '';
          position: absolute;
          left: 0;
          top: 0;
          width: 100%;
          height: 100%;
          transform: rotate(-2deg);
          border: 0.5px solid #000;
          border-radius: 5px;
          transition: all 0.3s ease-in-out;
        }

        &:hover::after {
          transform: rotate(2deg);
        }
      }

      .link__project {
        transition: all 0.3s ease-in-out;
        display: flex;
        align-items: center;

        span {
          display: inline-block;
          width: 22px;
          height: 22px;
          position: relative;
          background: url('../public/assets/images/svg/btn-treeangle.svg');
          background-repeat: no-repeat;
          background-position: center center;
          transition: all 0.3s ease-in-out;
          margin-right: 7px;

          &::after {
            transition: all 0.3s ease-in-out;
            position: absolute;
            transform: rotate(-14deg);
            left: 3px;
            top: 2px;
            content: url('../public/assets/images/svg/btn-treeangle-border.svg');
          }
        }

        &:hover {
          span::after {
            transform: rotate(14deg);
          }
        }
      }
    }
  }
}
</style>
