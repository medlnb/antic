<template>
  <section class="max-w-[1140px] mx-auto px-6 py-20 pt-10 lg:flex gap-20">
    <div class="flex-1 pb-10">
      <h1
        class="lg:text-[55px] tracking-tighter text-[45px] text-secondary font-light merriweather pb-[30px]"
      >
        We stay by your side to design your projects
      </h1>
      <NuxtLink to="/" class="text-[17px] text-primary font-bold karla"
        >Find out more ></NuxtLink
      >
    </div>
    <div class="flex-1 lg:grid flex flex-col lg:grid-cols-2 gap-4">
      <div v-for="item in data" :key="item.title">
        <h3 class="text-[25px] font-semibold text-primary dont-varta pb-3">
          {{ item.title }}
        </h3>
        <p class="text-[18px] text-success varta">
          {{ item.description }}
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Side to Design",
  data() {
    return {
      data: [
        {
          title: "Our Advices",
          description:
            "What if you took advantage of this rather special period to rethink your interior? You spend more time at home so you might as well feel good there.",
        },
        {
          title: "Click and Collect",
          description:
            "Adapted and contactless. Free from € 200 of purchases in stores offering the service.",
        },
        {
          title: "Conception Service",
          description:
            "Personalized service with an expert advisor for your interior and exterior decoration or layout projects. ",
        },
        {
          title: "Installation Service",
          description:
            "Our furniture packaged in flat packs are designed for easy assembly. But you can call on our partner.",
        },
      ],
    };
  },
};
</script>
