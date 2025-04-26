<template>
  <section class="max-w-[1140px] mx-auto px-6 py-20" id="next-section">
    <h2
      class="lg:text-[55px] text-[40px] font-light merriweather text-secondary"
    >
      Find your room
    </h2>
    <div class="lg:flex gap-6 lg:py-[48px] py-4">
      <p class="text-lg text-gray-500 lg:max-w-[165px] w-full pb-10">
        Dining room, bedroom, bathroom or office. Find what you need
      </p>
      <swiper
        :modules="modules"
        :breakpoints="{
          0: {
            slidesPerView: 1,
          },
          640: {
            slidesPerView: 1.5,
          },
          1024: {
            slidesPerView: 2,
          },
        }"
        :space-between="24"
        :navigation="{
          nextEl: '.rooms-next',
          prevEl: '.rooms-prev',
        }"
        :pagination="paginationOptions"
      >
        <swiper-slide v-for="room in rooms" :key="room.imageUrl">
          <div class="md:h-[340px] h-[230px] flex gap-8 relative">
            <h1
              class="w-1/3 text-center lg:text-[55px] text-[35px] merriweather text-primary absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"
            >
              {{ room.title }}
            </h1>
            <NuxtImg
              :src="room.imageUrl"
              alt="image"
              width="400"
              height="400"
              :custom="true"
              v-slot="{ src, isLoaded, imgAttrs }"
              class="md:w-[260px] w-[150px] object-cover object-center"
            >
              <img v-if="isLoaded" v-bind="imgAttrs" :src="src" />
              <div
                v-else
                class="bg-gray-200 loading-background md:w-[260px] w-[150px] h-full"
              ></div>
            </NuxtImg>

            <p
              v-if="room.isNew"
              class="text-[18px] text-success varta whitespace-nowrap"
            >
              New arrivals
            </p>
          </div>
        </swiper-slide>
      </swiper>
    </div>

    <div
      class="flex lg:flex-row flex-row-reverse lg:justify-start justify-between items-center pt-10"
    >
      <div class="lg:w-[190px] w-auto text-[18px] text-success varta">
        <p class="rooms-pagination" />
      </div>
      <button
        class="rooms-next text-primary text-[20px] karla font-bold flex gap-3 hover:gap-5 duration-200 cursor-pointer"
      >
        <span>Next</span>
        <span>></span>
      </button>
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
  name: "Rooms",
  components: {
    Swiper,
    SwiperSlide,
  },
  async setup() {
    const response = await fetch("https://antic-backend.vercel.app/api/room");
    const json = await response.json();
    const rooms = json.rooms;
    const modules = [Navigation, Pagination];
    const paginationOptions = {
      el: ".rooms-pagination",
      type: "fraction",
      renderFraction(currentClass, totalClass) {
        return `
            0<span class="${currentClass}"></span>
            /
            0<span class="${totalClass}"></span>
          `;
      },
    };
    return {
      modules,
      paginationOptions,
      rooms,
    };
  },
};
</script>
