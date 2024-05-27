 <template>
  <div>
    <HeaderPage />
    <MainSlider />
    <!-- <Carousel/> -->
    <FooterPage />
  </div>
</template> 

<script>
import HeaderPage from "../components/HeaderPage.vue";
import  FooterPage  from "../components/FooterPage.vue";
import MainSlider from "../components/MainSlider.vue";
// import Carousel from "~/components/Carousel.vue";
import '../public/assets/styles/styles.scss'
import '../public/assets/styles/adaptive.scss';

export default {
  components: {
    HeaderPage,
    FooterPage,
    MainSlider,
    // Carousel
  },
  name: "Main"
}
export async function getServerSideProps() {
  const response = await fetch('https://664878da2bb946cf2fa0af05.mockapi.io/api/v1/menu');
  const data = await response.json();
  console.log(data)
  return {
    props: {
      data,
    },
  };
}
</script> 
