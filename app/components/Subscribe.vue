<template>
  <section class="bg-white">
    <div
      class="lg:flex justify-between items-center max-w-[1140px] mx-auto px-6 pt-20"
    >
      <div>
        <h1
          class="text-[35px] text-[#121212] merriweather font-light mb-[15px]"
        >
          Be aware of the latest trends
        </h1>
        <h3 class="text-[18px] text-success varta mb-[10px]">
          Stay informed of new trends, but also of our various offers.
        </h3>
        <NuxtLink to="/" class="text-[17px] text-primary karla font-bold">
          {{ "Learn more >" }}</NuxtLink
        >
      </div>
      <div>
        <input
          type="email"
          v-model="email"
          placeholder="email@address.com"
          class="bg-[#F3EEE84D] text-[18px] text-success varta p-2 px-4 mr-4 mb-2 outline-none lg:w-auto w-full"
        />

        <button
          class="bg-[#534B42] text-white text-[17px] karla font-bold p-2 px-8 hover:opacity-70 duration-200 lg:w-auto w-11/12"
          @click="HandleSubscribe"
        >
          Subcribe
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Subscribe",
  data() {
    return {
      email: "",
    };
  },
  methods: {
    HandleSubscribe() {
      this.email = "";
    },
  },
};
</script>
