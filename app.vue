<template>
  <div>
    <Main></Main>
  </div>
</template>
<script lang="ts">
import './public/assets/styles/styles.scss'
import { defineComponent } from 'vue';
import Main from './pages/index.vue'
export default defineComponent({
  name: 'App',
  components: {
    Main
  },
});
</script>

