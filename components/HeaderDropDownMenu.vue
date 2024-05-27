<template>
  <div class="header__dropdown drop-menu">

    <button @click="toggleMenu" class="drop-menu__btn btn">
      <svg width="26" height="26" viewBox="0 0 26 26" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M0.812479 8.12499H25.1875C25.636 8.12499 25.9999 7.76096 25.9999 7.31251C25.9999 6.86399 25.6359 6.50003 25.1875 6.50003H0.812479C0.363961 6.50003 0 6.86406 0 7.31251C0 7.76096 0.364028 8.12499 0.812479 8.12499Z"
          fill="#444444" />
        <path
          d="M25.1875 12.1875H0.812479C0.363961 12.1875 0 12.5516 0 13C0 13.4484 0.364028 13.8125 0.812479 13.8125H25.1875C25.636 13.8125 25.9999 13.4484 25.9999 13C25.9999 12.5516 25.636 12.1875 25.1875 12.1875Z"
          fill="#444444" />
        <path
          d="M25.1875 17.875H8.93748C8.48896 17.875 8.125 18.239 8.125 18.6875C8.125 19.136 8.48903 19.5 8.93748 19.5H25.1875C25.636 19.5 25.9999 19.1359 25.9999 18.6875C26 18.239 25.636 17.875 25.1875 17.875Z"
          fill="#444444" />
      </svg>

    </button>
    <transition name="bounce" mode="out-in">
      <div class="drop-menu__block" v-if="isOpen">
        <div class="drop-menu__container container">
          <div class="header">
            <div class="container header__container">

              <HeaderLogo></HeaderLogo>
              <HeaderLang></HeaderLang>

              <button class=" btn drop-menu__close" @click="toggleMenu">
                <span>Close</span>
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path
                    d="M1.72353 19.1629L18.9592 1.92715C19.2764 1.61 19.2763 1.09523 18.9592 0.778132C18.6421 0.460982 18.1273 0.461028 17.8102 0.778132L0.574509 18.0138C0.257359 18.331 0.257407 18.8458 0.57451 19.1629C0.891612 19.48 1.40643 19.48 1.72353 19.1629Z"
                    fill="#444444" />
                  <path
                    d="M18.9591 17.8102L1.72344 0.574509C1.40628 0.257359 0.891522 0.257404 0.574423 0.574502C0.257325 0.891601 0.257328 1.40641 0.57443 1.72351L17.8101 18.9592C18.1273 19.2764 18.6421 19.2763 18.9591 18.9592C19.2762 18.6421 19.2763 18.1274 18.9591 17.8102Z"
                    fill="#444444" />
                </svg>

              </button>
            </div>
          </div>
          <HeaderDropItem :menuList="menuList"></HeaderDropItem>
          <FooterPage></FooterPage>
        </div>
      </div>
    </transition>
  </div>
</template>
<script>
import { defineComponent, ref } from 'vue';
import FooterPage from './FooterPage.vue';
import HeaderLang from './HeaderLang.vue';
import HeaderLogo from './HeaderLogo.vue';
import HeaderDropItem from './HeaderDropItem.vue';

export default defineComponent({
  name: 'DropdownMenu',
  components: [HeaderLang, HeaderLogo, HeaderDropItem, FooterPage],
  setup() {
    const isOpen = ref(false);
    const menuList = [
      {
        title: 'About us',
        imgUrl: '/assets/images/arh.png',
        isShowImg: false
      },
      {
        title: 'Interior',
        imgUrl: '/assets/images/decor.jpg',
        isShowImg: false

      },
      {
        title: 'Architecture',
        imgUrl: '/assets/images/arh.png',
        isShowImg: false

      },
      {
        title: 'Portfolio',
        imgUrl: '/assets/images/decor.jpg',
        isShowImg: false

      },
      {
        title: 'Contact',
        imgUrl: '/assets/images/arh.png',
        isShowImg: false

      },

    ]


    const toggleMenu = () => {
      isOpen.value = !isOpen.value;
    };

    return {
      isOpen,
      toggleMenu,
      menuList,
    };
  },
});
</script>
<style lang="scss">
.drop-menu {
  position: relative;
  z-index: 10;

  .footer__nav {
    justify-content: center;
  }

  &__container {
    width: 100%;
    min-height: 100vh;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;

  }

  &__btn {
    padding: 4px 6px;
    width: 38px;
    margin-left: 26px;
    background-color: #f3f3f3;
    border-radius: 5px;
  }

  &__block {
    position: fixed;
    width: 100%;
    min-height: 100%;
    right: 0;
    top: 0;
    left: 0;
    background: #fff url('../public/assets/images/bg.png');
    background-position: center center;
    background-size: cover;
    background-repeat: no-repeat;
  }

  &__close {
    font-size: 16px;
    display: flex;
    align-items: center;

    span {
      margin-right: 14px;
    }
  }

  &__list {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;

  }

  &__link {
    font-family: "PlayfairDisplay", sans-serif;
    font-size: 48px;
    line-height: 120%;
  }

  &__item {
    margin-bottom: 40px;
    position: relative;

    img {
      position: absolute;
      top: -100%;
      width: 216px;
      transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
    }
  }
}

.bounce-enter-active {
  animation: bounce-menu 0.7s;
}

.bounce-leave-active {
  animation: bounce-menu 0.5s reverse;
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

@keyframes bounce-menu {
  0% {
    transform: translateY(-50%);
    opacity: 0;
  }

  100% {
    transform: translateY(0);
    opacity: 1;
    // transform-origin: center right;
  }
}
</style>
