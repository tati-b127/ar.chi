<template>
    <footer class="footer ">
        <div class="container">
            <ul class="footer__nav">
                <li class="footer__item">
                    <a href="#" class="footer__link-soc">Facebook</a>
                </li>
                <li class="footer__item">
                    <a href="#" class="footer__link-soc">Vkontakte</a>
                </li>
                <li class="footer__item">
                    <a href="#" class="footer__link-soc">Behance</a>
                </li>
            </ul>
        </div>
    </footer>
</template>
<script>
export default {
    name: "Footer"
}
</script>
<style lang="scss">
.footer {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 120px;
    padding-top: 60px;
    padding-bottom: 60px;

    &__nav {
        display: flex;
        align-self: center;
    }

    &__item:not(:last-child) {
        margin-right: 35px;
    }
}
</style>