<template>
  <div
    class="navigation pin-t pin-x fixed"
    :class="{
      'navigation-white': hasBackground
    }"
  >
    <div class="container mx-auto flex justify-between h-16 items-center px-4">
      <a class="logo" href="/">
        <img :src="logoVariant" alt="CodePilot.ai Logo" class="h-10">
      </a>
      <!-- <button
        v-if="hasBackground"
        type="button"
        class="button button-primary m-0 ml-4 text-sm w-2/5 md:w-auto md:text-base"
        @click="$emit('open-download')"
      >
        Get CodePilot
      </button> -->
      <!-- <button
        type="button"
        class="button-fake md:hidden z-10 p-2"
        @click="toggleMenu"
      >
        <MenuIcon
          :fill="hasBackground || isOpenMenu ? '#000' : '#fff'"
        />
      </button> -->
      <!-- <div
        class="mobile-nav bg-white fixed pin-t pin-x flex flex-col pr-16 md:invisible"
        :class="{ 'is-open': isOpenMenu }"
      >
        <a class="mobile-link" href="/">About</a>
        <a class="mobile-link" href="/">Release Notes</a>
        <a class="mobile-link" href="/">Blog</a>
      </div> -->
    </div>
  </div>
</template>

<script>
import MenuIcon from './MenuIcon'
let lastScrollPosition = 0
let ticking = false

export default {
  name: 'Nav',
  components: { MenuIcon },
  data () {
    return {
      hasBackground: false,
      isOpenMenu: false
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  computed: {
    logoVariant () {
      return this.hasBackground
        ? require('../assets/codepilot-logo-dark.png')
        : require('../assets/codepilot-logo.png')
    }
  },
  methods: {
    handleScroll () {
      lastScrollPosition = window.scrollY

      if (!ticking) {
        window.requestAnimationFrame(() => {
          this.hasBackground = lastScrollPosition > 200
          ticking = false
        })

        ticking = true
      }
    },
    toggleMenu () {
      this.isOpenMenu = !this.isOpenMenu
    }
  }
}
</script>

<style lang="sass">
.navigation
  background-color: rgba(#fff, 0)
  transition: background-color 0.2s ease
  z-index: 10

  &.navigation-white
    background-color: rgba(#fff, 1)
    box-shadow: 0 3px 10px 0 rgba(#000, 0.1)

    .link
      color: #3C4150

.button-fake
  background: none
  border: none

.mobile-nav
  transition: transform .2s ease
  transform: translateY(-100%)

.is-open
  transform: translateY(0)
</style>
