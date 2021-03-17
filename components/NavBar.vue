<template>
  <header
    class="navbar bg-theme-white bg-opacity-95 z-50 shadow-sm"
    :class="{ 'hidden-navbar': !showNavbar }"
  >
    <transition name="fade">
      <div class="flex justify-between text-xl py-3 px-5 sm:px-10 md:px-32">
        <p
          v-if="$store.state.menu === 'Please create a menu document'"
          class="logo"
        >
          {{ $store.state.menu }}
        </p>
        <nuxt-link to="/" class="logo">{{
          $prismic.asText($store.state.menu.title)
        }}</nuxt-link>
        <nav>
          <ul>
            <li
              v-for="menuLink in $store.state.menu.menu_links"
              :key="menuLink.id"
            >
              <prismic-link :field="menuLink.link">{{
                $prismic.asText(menuLink.label)
              }}</prismic-link>
            </li>
          </ul>
        </nav>
        <!-- <nav
        class="flex justify-between items-center py-3 px-5 sm:px-10 md:px-32 text-gray-800"
      >
        <NuxtLink to="/" class="flex items-center pl-5 md:pl-8 tracking-widest">
          Conor O'Rourke
        </NuxtLink>
        <div class="flex items-center"> -->

        <!-- <a
            v-scroll-to="'#work-section'"
            href="#"
            class="link uppercase text-lg tracking-wide pl-6 md:pl-16"
          >
            <span
              class="border border-theme-black rounded block py-2 px-3 transition-all duration-200 ease-out md:hover:bg-theme-black md:hover:text-theme-white"
            >
              work
            </span>
          </a> -->
        <!-- </div>
      </nav> -->
      </div>
    </transition>
  </header>
</template>

<script>
export default {
  name: 'NavBar',
  components: {},
  data() {
    return {
      showNavbar: true,
      lastScrollPosition: 0,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    onScroll() {
      // Get the current scroll position
      const currentScrollPosition =
        window.pageYOffset || document.documentElement.scrollTop

      // Because of momentum scrolling on mobiles, we shouldn't continue if it is less than zero
      if (currentScrollPosition < 0) {
        return
      }

      // Stop executing this function if the difference between
      // current scroll position and last scroll position is less than some offset
      if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 60) {
        return
      }

      // Here we determine whether we need to show or hide the navbar
      this.showNavbar = currentScrollPosition < this.lastScrollPosition

      // Set the current scroll position as the last scroll position
      this.lastScrollPosition = currentScrollPosition
    },
  },
}
</script>

<style lang="scss" scoped>
.navbar {
  height: 100px;
  width: 100vw;
  position: fixed;

  /* box-shadow: 0 2px 15px rgba(71, 120, 120, 0.5); */
  transform: translate3d(0, 0, 0);
  transition: 0.1s all ease-out;
}
.navbar.hidden-navbar {
  box-shadow: none;
  transform: translate3d(0, -100%, 0);
}
</style>
