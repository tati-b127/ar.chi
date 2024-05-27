<template>
  <div class="header__search search">
    <button class="btn search__btn" @click="showSearch">
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
        <g clip-path="url(#clip0_0_24)">
          <path
            d="M19.8248 18.98L14.9645 14.1197C16.2683 12.6208 17.0576 10.6652 17.0576 8.52772C17.0576 3.82262 13.2306 0 8.52994 0C3.82484 0 0.00222778 3.82705 0.00222778 8.52772C0.00222778 13.2284 3.82928 17.0554 8.52994 17.0554C10.6674 17.0554 12.6231 16.2661 14.122 14.9623L18.9823 19.8226C19.0976 19.9379 19.2528 20 19.4035 20C19.5543 20 19.7095 19.9424 19.8248 19.8226C20.0554 19.592 20.0554 19.2106 19.8248 18.98ZM1.19513 8.52772C1.19513 4.48337 4.48559 1.19734 8.5255 1.19734C12.5698 1.19734 15.8559 4.4878 15.8559 8.52772C15.8559 12.5676 12.5698 15.8625 8.5255 15.8625C4.48559 15.8625 1.19513 12.5721 1.19513 8.52772Z"
            fill="#444444" />
        </g>
        <defs>
          <clipPath id="clip0_0_24">
            <rect width="20" height="20" fill="white" />
          </clipPath>
        </defs>
      </svg>
    </button>
    <transition name="bounce" mode="out-in">
      <div class="search__block" v-if="isOpen">
        <button class="btn search__btn" @click="search">
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g clip-path="url(#clip0_0_24)">
              <path
                d="M19.8248 18.98L14.9645 14.1197C16.2683 12.6208 17.0576 10.6652 17.0576 8.52772C17.0576 3.82262 13.2306 0 8.52994 0C3.82484 0 0.00222778 3.82705 0.00222778 8.52772C0.00222778 13.2284 3.82928 17.0554 8.52994 17.0554C10.6674 17.0554 12.6231 16.2661 14.122 14.9623L18.9823 19.8226C19.0976 19.9379 19.2528 20 19.4035 20C19.5543 20 19.7095 19.9424 19.8248 19.8226C20.0554 19.592 20.0554 19.2106 19.8248 18.98ZM1.19513 8.52772C1.19513 4.48337 4.48559 1.19734 8.5255 1.19734C12.5698 1.19734 15.8559 4.4878 15.8559 8.52772C15.8559 12.5676 12.5698 15.8625 8.5255 15.8625C4.48559 15.8625 1.19513 12.5721 1.19513 8.52772Z"
                fill="#444444" />
            </g>
            <defs>
              <clipPath id="clip0_0_24">
                <rect width="20" height="20" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </button>
        <input class="search__input" type="text" name="search" placeholder="What are you looking for?" />
        <button class="btn search__close" @click="showSearch">
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M1.23526 13.5925L13.5882 1.36697C13.8155 1.14201 13.8155 0.776878 13.5882 0.551953C13.3609 0.326994 12.9919 0.327028 12.7647 0.551953L0.411754 12.7775C0.184451 13.0024 0.184485 13.3676 0.411754 13.5925C0.639023 13.8174 1.00799 13.8174 1.23526 13.5925Z"
              fill="#444444" />
            <path
              d="M13.5884 12.633L1.23548 0.407508C1.00818 0.182549 0.639248 0.18258 0.411982 0.407503C0.184715 0.632425 0.184718 0.997588 0.411986 1.22251L12.7649 13.4481C12.9922 13.673 13.3611 13.673 13.5884 13.4481C13.8157 13.2231 13.8157 12.858 13.5884 12.633Z"
              fill="#444444" />
          </svg>
        </button>
      </div>
    </transition>
  </div>
</template>
<script>
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "HeaderSearch",
  setup() {
    let isOpen = ref(false);
    const showSearch = () => {
      isOpen.value = isOpen.value ? false : true;
      // isMenuOpen.value = !isMenuOpen.value;
    };
    const search = () => {
      console.log("Search...");
    };
    return { isOpen, showSearch, search };
  },
});
</script>
<style lang="scss">
.header__nav-search {
  position: relative;
  display: flex;
  align-items: center;
  padding: 6px 0;
  background-color: #f3f3f3;
  border-radius: 5px;
}

.search {
  display: flex;
  align-items: center;
  padding: 0px 20px;
  border-left: 2px solid #00000020;
  border-right: 2px solid #00000020;

  &__block {
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: space-between;
    right: -1px;
    max-width: 586px;
    width: 100%;
    height: 25px;
    transition: all 0.3s ease-in;
    background-color: #f3f3f3;
    padding: 0 10px;
    border-left: 2px solid #00000020;
    border-right: 2px solid #00000020;

    &::after {
      content: "";
      position: absolute;
      width: calc(100% - 20px);
      height: 2px;
      bottom: -10px;
      background-color: #00000020;
      transition: all 0.1s;
    }
  }

  &__input {
    width: 100%;
    max-width: 480px;
    font-size: 16px;
    background: #f3f3f3;
    padding: 2px 20px;
    border: none;
    outline: none;
  }

  &__close {
    padding: 6px 10px;
  }

  &__btn {
    height: 25px;
  }
}

.bounce-enter-active {
  animation: bounce-in 0.7s;
}

.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: translateY(-150%);
    opacity: 0;
  }

  100% {
    transform: translateY(0);
    opacity: 1;
  }
}
</style>
