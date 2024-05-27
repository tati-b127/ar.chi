<template>
    <nav class="header__menu menu">
        <ul class="menu__list">
            <li class="menu__item">
                <a href="/about" class="menu__link">About us</a>
            </li>
            <li class="menu__item">
                <a href="/architecture" class="menu__link">Architecture</a>
            </li>
            <li class="menu__item">
                <a href="/interior" class="menu__link">Interior</a>
            </li>
            <li class="menu__item">
                <a href="/contacts" class="menu__link">Contact</a>
            </li>
            <li class="menu__item">
                <a href="/shop" class="menu__link">Shop</a>
            </li>
        </ul>
    </nav>
</template>
<script>
export default {
  name: "HeaderMenu"
}
</script>
<style lang="scss">
.menu {
    display: flex;
    margin-right: 40px;
    &__list {
        list-style: none;
        display: flex;
        justify-content: space-between;
        max-width: 450px
    }
    &__item:not(:last-child) {
        margin-right: 40px;
    }
    &__link {
        color: #444444;
        font-size: 16px;
        line-height: 120%;
    }
}
</style>