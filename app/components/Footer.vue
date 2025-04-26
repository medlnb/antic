<template>
  <footer class="max-w-[1140px] mx-auto px-6 py-10">
    <h2
      class="pb-6 md:block lg:hidden hidden text-center text-[34px] text-[#534B42] merriweather font-bold"
    >
      antic
    </h2>
    <section class="lg:flex justify-between lg:flex-row md:grid md:grid-cols-3">
      <h2
        class="pb-6 md:hidden lg:block lg:text-start text-center text-[34px] text-[#534B42] merriweather font-bold"
      >
        antic
      </h2>

      <div v-for="footer in footers" :key="footer.title" class="pb-6">
        <h2 class="pb-6 text-[25px] text-[#534B42] varta font-semibold">
          {{ footer.title }}
        </h2>
        <ul>
          <li
            v-for="subtitle in footer.subtitles"
            :key="subtitle"
            class="text-[18px] text-secondary varta mb-2"
          >
            <NuxtLink to="/">
              {{ subtitle }}
            </NuxtLink>
          </li>
        </ul>
      </div>
      <div class="lg:w-[235px] w-full pb-6">
        <h2
          class="pb-6 text-[25px] text-[#534B42] varta font-semibold whitespace-nowrap"
        >
          We respect our planet
        </h2>
        <img
          alt="environmentalist"
          src="/images/environmentalist.jpg"
          class="w-full mb-2"
        />
        <p class="text-[16px] text-secondary varta">
          We’re taking positive steps to reduce our impact on the planet. For
          us, that means retailing responsibly.
        </p>
        <NuxtLink
          to="/"
          class="mt-2 text-[17px] text-primary karla font-bold flex gap-3 hover:gap-5 duration-200 cursor-pointer"
        >
          <span>Learn more</span>
          <span>></span>
        </NuxtLink>
      </div>
    </section>
    <section class="py-8">
      <div class="flex justify-center gap-6">
        <img
          alt="Facebook"
          src="../assets/svg/Facebook.svg"
          class="hover:scale-110 duration-200 cursor-pointer"
        />
        <img
          alt="twitter"
          src="../assets/svg/Twitter.png"
          class="hover:scale-110 duration-200 cursor-pointer"
        />
        <img
          alt="linkedin"
          src="../assets/svg/Linkedin.png"
          class="hover:scale-110 duration-200 cursor-pointer"
        />
        <img
          alt="Instagram"
          src="../assets/svg/Instagram.png"
          class="hover:scale-110 duration-200 cursor-pointer"
        />
      </div>
    </section>
    <section
      class="flex md:flex-row flex-col-reverse justify-between text-secondary opacity-70 varta text-[18px]"
    >
      <p>© 2021 Agence Dnd</p>
      <ul class="flex flex-wrap gap-x-8 pb-6">
        <li>Privacy policy</li>
        <li>Term of service</li>
        <li>Language</li>
      </ul>
    </section>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      footers: [
        {
          title: "Products",
          subtitles: [
            "Furniture",
            "Decoration",
            "Storage",
            "Baby and child",
            "Connected home",
          ],
        },
        {
          title: "Rooms",
          subtitles: [
            "Living room",
            "Dining room",
            "Cooked",
            "Bedroom",
            "Bathroom",
            "Office",
            "Laundry",
            "Garage",
          ],
        },
        {
          title: "Services",
          subtitles: [
            "Click and collect",
            "Conception",
            "Installation",
            "Advices",
            "Gift card",
          ],
        },
        {
          title: "About",
          subtitles: ["Our story", "Our stores", "Our partners"],
        },
      ],
    };
  },
};
</script>
