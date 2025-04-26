<template>
  <header class="flex justify-between items-center">
    <nav>
      <ul class="flex items-center gap-8">
        <li
          class="text-[34px] merriweather lg:text-primary text-white font-bold hover:scale-105 duration-200 cursor-pointer"
        >
          <NuxtLink to="/">antic</NuxtLink>
        </li>
        <li
          v-for="link in navLinks"
          :key="link.label"
          class="hover:px-2 hover:font-semibold text-[18px] text-secondary varta duration-200 cursor-pointer hidden lg:block"
        >
          <NuxtLink :to="link.path">{{ link.label }}</NuxtLink>
        </li>
      </ul>
    </nav>

    <div class="relative">
      <!-- href="tel:911"-->
      <img
        src="../assets/svg/Contact.svg"
        alt="Contact"
        class="hover:scale-125 duration-200 cursor-pointer hidden lg:block"
      />
      <button
        class="hover:scale-125 duration-200 cursor-pointer lg:hidden text-5xl"
        @click="handleToggleMenu"
      >
        =
      </button>
      <ul v-if="toggleMenu" class="absolute top-full right-0">
        <li
          v-for="link in navLinks"
          :key="link.label"
          class="lg:hidden text-end text-xl whitespace-nowrap"
        >
          <NuxtLink :to="link.path">{{ link.label }} -</NuxtLink>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      navLinks: [
        { label: "Products", path: "/" },
        { label: "Rooms", path: "/" },
        { label: "Services", path: "/" },
        { label: "Inspirations", path: "/" },
        { label: "Admin", path: "/admin" },
      ],
      toggleMenu: false,
    };
  },
  methods: {
    handleToggleMenu() {
      this.toggleMenu = !this.toggleMenu;
    },
  },
};
</script>
