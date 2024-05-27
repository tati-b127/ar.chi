<template>
    <div class="header__lang">
        <button class="btn btn__lang" :class="{ btn__lang_active: isRu }" @click="changeLang">RUS</button>
        <button class="btn btn__lang" :class="{ btn__lang_active: isEng }" @click="changeLang">ENG</button>
    </div>
</template>
<style lang="scss">
.header__lang {
    display: flex;
    padding: 0 0 0 32px;
    border-left: 2px solid #00000020;
    margin-right: auto;
}

.btn__lang {
    font-size: 16px;
    padding: 6px;
    border-radius: 5px;
    background: transparent;
    color: #44444490;
    margin-right: 14px;
    transition: all 0.3s ease-in-out;

    &_active {
        color: #333333;
        background: #4A642420;
    }
}
</style>
<script>
export default defineComponent({
    setup() {
        const isEng = ref(true);
        const isRu = ref(false);
        const changeLang = () => {
            if (isRu) {
                isRu.value = !isRu.value;
                isEng.value = !isEng.value;
                //продолжение логики
            } else {
                isRu.value = !isRu.value;
                isEng.value = !isEng.value;
                //продолжение логики
            }
        }
        return { changeLang, isRu, isEng }
    }
})

</script>