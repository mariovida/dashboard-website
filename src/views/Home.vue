<template>
  <div class="home">
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

    <h1 class="block-effect" style="--td: 1.2s">
      <div class="block-reveal title" style="--bc: #4040bf; --d: .1s">Make a move</div>
      <div class="block-reveal desc" style="--bc: #bf4060; --d: .5s">Join our growing community</div>
    </h1>
    <div class="reg">
      <router-link to="/login" target="self"
        ><button id="login">LOG IN</button></router-link
      >
      <router-link to="/register" target="self"
        ><button id="signup">SIGN UP</button></router-link
      >
    </div>
    <img src="../assets/startup.svg" class="startup_image"/>

    <div class="goals">
      <h1>Our goals</h1>
      <div class="timeline">
        <div class="goal-left">
          <div class="content">
            <h2>Make a budget and live by it</h2>
            <p>
              Budgets are focused on debts and expenses and nobody got rich by
              focusing on their debts. You get wealthy by focusing on your
              assets and your income. Most experts agree that budgets are
              useful, if only to clearly define the amount of income and fixed
              expenses in someone’s household. Creating a budget is a great
              way to know your financial limits.
            </p>
          </div>
        </div>
        <div class="goal-right">
          <div class="content">
            <h2>Saving an emergency fund</h2>
            <p>
              In a fragile job market, emergency funds are essential.
              Emergency funds are commonly used to fix a surprise car repair,
              pay for a hospital stay, the mortgage, and a variety of other
              unforeseen issues.
            </p>
          </div>
        </div>
        <div class="goal-left">
          <div class="content">
            <h2>Prioritize expenses and goals</h2>
            <p>
              Understand the difference between needs and wants, then focus on
              the essentials first. That doesn’t mean other expenses aren’t
              important, though. Your financial goals, such as paying off debt
              or saving for retirement, should still receive attention. The
              purpose of a budget, is to understand whether or not your money
              is going toward things that you’re happy with, you’re proud of
              and align with your values.
            </p>
          </div>
        </div>
      </div>
      <div class="goal-right">
        <div class="content">
          <h2>Leave room for surprises</h2>
          <p>
            Don’t expect your budget to be perfect. Surprises will happen, and
            some expenses may slip through the cracks — like the occasional
            impulse buy. But you can take precautions to soften the blow.
          </p>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'

export default {
  name: 'App',
  components: {
    Footer
  },
  data() {
    return {
      hamburgerOpen: false,
    }
  }
}
</script>

<style>
@import "../style.css";
</style>
