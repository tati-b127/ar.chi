<template>
  <header class="header">
    <div class="header__container container">
      <HeaderLogo></HeaderLogo>
      <HeaderLang></HeaderLang>
      <div class="header__nav-search">
        <HeaderMenu></HeaderMenu>
        <HeaderSearch></HeaderSearch>
      </div>
      <HeaderDropDownMenu />
    </div>
  </header>
</template>
<script>
import HeaderMenu from "./HeaderMenu.vue";
import HeaderLogo from "./HeaderLogo.vue";
import HeaderSearch from "./HeaderSearch.vue";
import HeaderLang from "./HeaderLang.vue";
import HeaderDropDownMenu from "./HeaderDropDownMenu.vue";
export default {
  name: "HeaderPage",
  components: {
    HeaderLogo,
    HeaderLang,
    HeaderMenu,
    HeaderSearch,
    HeaderDropDownMenu,
  },
};
</script>

<style lang="scss">
.header {
  padding: 34px 0;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
  height: 100px;

  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }


}
</style>
