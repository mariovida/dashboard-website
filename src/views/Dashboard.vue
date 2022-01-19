<template>
  <div class="main">
    <div class="nav-background"></div>
    <div v-if="user" class="left-nav">
      <div><img src="../assets/man.png" /></div><h1>{{ user.data.displayName }}</h1>
      <div class="left-nav-buttons">
        <router-link to="/dashboard" target="self">Analytics</router-link><br/>
        <router-link to="/todo" target="self">To Do</router-link><br/>
        <a @click.prevent="signOut">Sign out</a>
      </div>
    </div>

  </div>
</template>

<script>
import { mapGetters } from "vuex";
import firebase from 'firebase/compat/app';
import 'firebase/compat/auth';

export default {
  name: 'main',
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
  background-color: #F2F2F2;
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
</style>
