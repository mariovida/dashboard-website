<template>
  <div id="app">
    <div :class="{ change_color: scrollPosition > 120 }">
      <div id="nav">
        <router-link to="/">Home</router-link>
        <router-link v-if="user" to="/dashboard">Dashboard</router-link>
        <router-link to="/about">About</router-link>
        <router-link to="/contact">Contact</router-link>
      </div>
    </div>

    <router-view/>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  data() {
    return {
      scrollPosition: null,
    };
  },
  computed: {
    // map `this.user` to `this.$store.getters.user`
    ...mapGetters({
      user: "user"
    })
  },
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY;
    },
  },
  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
#app {
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  position: fixed;
  top: -3px;
  right: 10px;
  z-index: 10;
}
#nav a {
  font-family: "Poppins";
  text-decoration: none;
  font-size: 17px;
  color: #F2F2F2;
  border: 2px solid #333;
  border-radius: 8px;
  padding: 5px 18px;
  margin-left: 18px;
  transition: 0.3s;
}
#nav a.router-link-exact-active {
  background-color: #333;
}
.change_color {
  position: fixed;
  top: 0;
  width: 100%;
  height: 80px;
  z-index: 2;
  background-color: #333;
  transition: 0.4s;
}
.change_color #nav a {
  color: #F2F2F2;
  border-color: #F2F2F2;
  padding: 5px 18px;
}
.change_color #nav a:hover {
  background-color: #404040;
}
@media screen and (max-width: 768px) {
  #nav {display: none;}
  .change_color { display: none;}
}
</style>
