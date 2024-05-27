<template>
    <ul class="drop-menu__list">
        <li class="drop-menu__item" v-for="(item, index) in menuList" :key="item.id">
            <a href="#" @mouseover="(e) => onHover(e)" @mouseleave="(e) => onDefault(e)" class="drop-menu__link">{{
            item.title }}</a>
            <transition name="slide-fade" mode="out-in">
                <img class="hide" :class="{ left: index % 2 === 1 }" :src="item.imgUrl" :alt="item.title">
            </transition>
        </li>
    </ul>

</template>
<script>
export default {
    props: ["menuList"],

    setup() {
        const isShow = ref(true);
        const onHover = (e) => {
            const img = e.target.parentNode.children[1]
            img.classList.remove('hide')
            img.classList.add('show')
        }
        const onDefault = (e) => {
            const img = e.target.parentNode.children[1]
            img.classList.add('hide')
            img.classList.remove('show')
        }
        return {
            onHover,
            onDefault,
            isShow,
        }
    }
}</script>
<style>
.hide {
    opacity: 0;
    transform: translateX(50px);
}

.show {
    opacity: 1;
    transform: translateX(0);
}

.left.hide {
    transform: translateX(-250px);
    right: 0;
}
.left.show {
    transform: translateX(-200px);
    right: 0;
}
</style>