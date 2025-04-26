<template>
  <main class="bg-[#F3EEE8]">
    <Hero />
    <Rooms />
    <SidetoDesign />
    <Subscribe />
    <Inspirations />
    <Footer />
  </main>
</template>
<script>
import Hero from "../components/Hero.vue";
import Footer from "../components/Footer.vue";
import Subscribe from "../components/Subscribe.vue";
import Inspirations from "../components/Inspirations.vue";
import Rooms from "../components/Rooms.vue";

export default {
  name: "App",
  components: {
    Hero,
    Footer,
    Subscribe,
    Inspirations,
    Rooms,
  },
};
</script>
