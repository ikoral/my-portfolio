<template>
  <div
    class="font-sans text-gray-800 leading-normal flex flex-col min-h-screen"
  >
    <header class="border-t-14 border-blue">
      <nav class="container mx-auto flex justify-between items-center py-8">
        <a href="/" class="text-4xl" id="ilhan"
          ><span class="text-blue font-bold">ilhan</span>koral</a
        >
        <ul class="uppercase tracking-wide font-bold flex items-center">
          <li class="mr-8">
            <a
              href="/#projects"
              v-scroll-to="{ el: '#projects', offset: +50 }"
              class="text-gray-800 hover:text-gray-600 hover:font-bold"
              >Projects</a
            >
          </li>
        </ul>
      </nav>
    </header>
    <div class="flex-grow">
      <slot />
    </div>

    <footer class="bg-blue text-white">
      <div
        class="container mx-auto flex items-center justify-between py-4 text-xs"
      >
        <div>&copy; 2021 | by Ilhan KORAL</div>
        <ul class="flex items-center">
          <li class="mr-8">
            <a href="https://www.linkedin.com/in/ilhankoral" target="_blank">
              <img src="../../static/linkedin.svg" alt="" /><img />
            </a>
          </li>
          <li>
            <a href="https://twitter.com/KoralIlhan" target="_blank">
              <img src="../../static/twitter.svg" alt="" />
            </a>
          </li>
          <li class="ml-10">
            <g-link to="/" v-scroll-to="{ el: '#ilhan', offset: -50 }">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M5 15l7-7 7 7"
                />
              </svg>
            </g-link>
          </li>
        </ul>
      </div>
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import SearchInput from "../components/SearchInput";
import ThemeSwitcher from "../components/ThemeSwitcher";

export default {
  components: {
    SearchInput,
    ThemeSwitcher,
  },
  mounted() {
    this.theme = localStorage.getItem("theme") || "theme-light";
  },
  data() {
    return {
      isOpen: false,
      theme: "",
    };
  },
  methods: {
    scrollToTop() {
      window.scrollTo(0, 0);
    },
    toggle() {
      this.isOpen = !this.isOpen;
    },
    updateTheme(theme) {
      this.theme = theme;
    },
  },
};
</script>

<style src="../css/main.css" />
