<template>
  <div class="dashboard">
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

    <div class="nav-background"></div>
    <div v-if="user" class="left-nav">
      <div><img src="../assets/man.png" /></div><h1>{{ user.data.displayName }}</h1>
      <div class="left-nav-buttons">
        <router-link to="/dashboard" target="self">Analytics</router-link><br/>
        <router-link to="/todo" target="self">To Do</router-link><br/>
        <a @click.prevent="signOut">Sign out</a>
      </div>
    </div>

    <ChartPie class="chart-pie "/>
    <ChartArea class="chart-area" />
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import firebase from 'firebase/compat/app';
import 'firebase/compat/auth';
import ChartPie from '../components/ChartPie.vue'
import ChartArea from '../components/ChartLine.vue'

export default {
  name: 'main',
  components: {
    ChartPie,
    ChartArea
  },
  data() {
    return {
      hamburgerOpen: false,
    }
  },
  computed: {
    ...mapGetters({
      user: "user"
    })
  },
  methods: {
    signOut() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.replace({
            name: "Home"
          });
        });
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
* {
  scroll-behavior: smooth;
  box-sizing: border-box;
  font-family: "Poppins";
  padding: 0;
  margin: 0;
}
.dashboard {
  background-color: #F2F2F2;
}
.hamburger__item {
  background: #F2F2F2;
}
.nav-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  background-color: #333;
}
.left-nav {
  width: 280px;
  height: 100vh;
  background-color: #CCC;
}
.left-nav img {
  width: 40px;
  height: 40px;
  position: absolute;
  top: 20px;
  left: 20px;
  background-color: transparent;
}
h1 {
  position: absolute;
  left: 80px;
  font-size: 35px;
  font-weight: 600;
  color: #F2F2F2;
  padding: 15px 0;
  background-color: transparent;
}
.left-nav-buttons {
  background-color: transparent;
  position: absolute;
  top: 120px;
  left: 40px;
}
.left-nav-buttons a {
  display: block;
  width: 200px;
  padding: 10px 0;
  background-color: #CCC;
  color: #333;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  border: 2px solid #333;
  border-radius: 6px;
  cursor: pointer;
}
.left-nav-buttons a:hover {
  background-color: #404040;
  color: #F2F2F2;
}
.left-nav-buttons a.router-link-exact-active {
  background-color: #333;
  color: #F2F2F2;
}
.left-nav-buttons a.router-link-exact-active:hover {
  background-color: #404040;
}
.chart-pie, .chart-area {
  width: 450px;
  position: absolute;
  top: 110px;
  left: 310px;
  border: 2px solid #333;
  border-radius: 8px;
  padding: 20px;
}
.chart-area {
  width: 450px;
  left: 790px;
  padding: 30px 20px;
}
@media screen and (max-width: 768px) {
  .dropic.droper-content {
    top: 100px;
  }
  .left-nav {
    width: 0;
  }
  .left-nav-buttons a {
    display: none;
  }
  .chart-pie, .chart-area {
    width: 90%;
    top: 120px;
    left: 5%;
    border: 0;
    border-bottom: 2px solid #333;
    border-radius: 0;
    padding: 0 0 20px 0;
  }
  .chart-area {
    top: 335px;
  }
}
</style>
