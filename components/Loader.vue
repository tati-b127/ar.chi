<template>
    <div class="loader-wrap">
        <span class="loader">
        </span>
    </div>

</template>
<style>
.loader-wrap {
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #f3f3f3;
}

.loader {
    width: 54px;
    height: 54px;
    display: inline-block;
    position: relative;
}

.loader::after,
.loader::before {
    content: '';
    box-sizing: border-box;
    width: 48px;
    height: 48px;
    border-radius: 50%;
    border: 1px solid #425A20;
    position: absolute;
    left: 0;
    top: 0;
    animation: animloader 2s linear infinite;
}

.loader::after {
    animation-delay: 1s;
}

@keyframes animloader {
    0% {
        transform: scale(0);
        opacity: 1;
    }

    100% {
        transform: scale(1);
        opacity: 0;
    }
}
</style>
<script>
export default {
    name: 'Loader'
}</script>
