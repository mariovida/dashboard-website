<template>
  <div class="about">
    <div
      class="hamburger"
      @click="hamburgerOpen = !hamburgerOpen"
      :class="hamburgerOpen ? 'hamburger--is-open' : ''"
    >
      <div class="hamburger__item hamburger__item--first"></div>
      <div class="hamburger__item hamburger__item--middle"></div>
      <div class="hamburger__item hamburger__item--last"></div>
    </div>
    <div class="droper-content" :class="hamburgerOpen ? 'dropic' : ''">
      <router-link to="/">HOME</router-link>
      <router-link to="/dashboard">DASHBOARD</router-link>
      <router-link to="/about">ABOUT</router-link>
      <router-link to="/contact">CONTACT</router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hamburgerOpen: false,
    }
  }
}
</script>
