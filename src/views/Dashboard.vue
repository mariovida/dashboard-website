<template>
  <div class="main">
    <div v-if="user" class="left-nav">
      <div class="img-avatar"><img src="../assets/man.png" /></div><h1>{{ user.data.displayName }}</h1>
      <router-link to="/todo" target="self"
        ><button id="todo">To Do</button></router-link
      >
    </div>
    <div class="nav-item">{{user.data.displayName}}</div>
    <a class="nav-link" @click.prevent="signOut">Sign out</a>
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
.left-nav {
  width: 20%;
  height: 100vh;
  background-color: #333;
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
</style>
