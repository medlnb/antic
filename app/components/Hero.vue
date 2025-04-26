<template>
  <div class="h-svh relative lg:text-black text-white">
    <!-- background -->
    <img
      src="/images/heroBg.jpg"
      class="lg:w-1/2 w-full h-full object-cover top-0 right-0 absolute"
    />

    <!-- content -->
    <main class="max-w-[1140px] mx-auto px-6 lg:py-20 py-6 relative z-10 flex flex-col h-full">
      <Nav />
      <section class="flex-1 flex flex-col justify-center lg:w-1/2 lg:mx-0 mx-auto w-full"> 
        <div class="max-w-[420px] lg:mx-0 mx-auto">
          <h3 class="varta font-bold text-[14px] lg:text-primary text-white lg:text-start text-center mb-[50px]">HOME DESIGN</h3>
          <h1 class="merriweather font-light text-[50px] lg:text-primary text-white lg:text-start text-center mb-[30px]">Elegance for Interiors & Exteriors</h1>
          <h2 class="varta  text-[22px] lg:text-success text-white lg:text-start text-center mb-[48px]">We provide everyone with modern, trendy, quality furniture</h2>
          <img alt="scroll down" src="../assets/svg/Scroll Down.svg" class="mx-0 hidden lg:block" @click="scrollToSection"></img>
          <img alt="scroll down" src="../assets/svg/Scroll Downl.svg" class="mx-auto lg:hidden" @click="scrollToSection"></img>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import Nav from "../components/Nav.vue";
export default {
  name: "Hero",
  components: {
    Nav,
  },
  methods: {
    scrollToSection() {
      const section = document.getElementById("next-section");
      if (section) 
        section.scrollIntoView({ behavior: "smooth" });
      
    },
  },

};
</script>
