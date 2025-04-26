<template>
  <section class="bg-white">
    <div
      class="lg:max-w-[calc(100svw-(100svw-1140px)/2)] lg:ml-[calc((100svw-1140px)/2)] px-6 py-10 lg:px-0 pt-20 flex flex-col-reverse lg:flex-col"
    >
      <div class="lg:block hidden">
        <swiper
          :modules="modules"
          :slides-per-view="2.5"
          :space-between="50"
          :navigation="{
            nextEl: '.swiper-next',
            prevEl: '.swiper-prev',
          }"
          :pagination="paginationOptions"
        >
          <swiper-slide v-for="image in images" :key="image.label">
            <div class="h-[460px] lg:h-[600px]">
              <img
                class="h-full w-full object-cover object-center"
                :src="image.src"
                alt="Inspiration Image"
              />
            </div>
          </swiper-slide>
        </swiper>
      </div>

      <div class="lg:hidden grid md:grid-cols-3 grid-cols-2 gap-6">
        <div v-for="room in images" :key="room.label">
          <img
            class="h-72 w-full object-cover object-center"
            :src="room.src"
            :alt="room.label"
          />
          <h2 class="py-4 text-xl font-semibold text-black">
            {{ room.label }}
          </h2>
        </div>
      </div>

      <div class="lg:flex justify-between items-start mt-8 lg:pr-28">
        <h1 class="text-[45px] text-[#534B42] merriweather font-light flex-1">
          Inspirations
        </h1>
        <p class="flex-1 text-[18px] text-secondary varta mb-8">
          Our experts are keen to stay on top of trends in order to offer you
          new inspirations for your interior and exterior every day. Remember
          that to inspire you we have to inspire ourselves and we want to share
          that with you.
        </p>
        <div class="flex-1 lg:flex hidden justify-center">
          <div>
            <div class="flex gap-4">
              <img
                class="swiper-prev"
                alt="swiper-prev"
                src="../assets/svg/Left.png"
              />
              <img
                class="swiper-next"
                alt="swiper-next"
                src="../assets/svg/Right.png"
              />
            </div>
            <div class="pagination text-[18px] text-success varta mt-4" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

export default {
  name: "Inspirations",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const modules = [Navigation, Pagination];

    const paginationOptions = {
      el: ".pagination",
      type: "fraction",
      renderFraction(currentClass, totalClass) {
        return `
          0<span class="${currentClass}"></span>
          /
          0<span class="${totalClass}"></span>
        `;
      },
    };

    const images = [
      {
        label: "Chair",
        src: "/images/Inspirations1.jpg",
      },
      {
        label: "Cooked",
        src: "/images/Inspirations2.jpg",
      },
      {
        label: "Tables",
        src: "/images/Inspirations3.jpg",
      },
      {
        label: "Living room",
        src: "/images/Inspirations4.png",
      },
    ];

    return {
      modules,
      paginationOptions,
      images,
    };
  },
};
</script>
