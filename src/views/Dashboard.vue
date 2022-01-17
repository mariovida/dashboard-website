<template>
  <div class="main">
    <h1>Welcome, {{ this.name }}</h1>
    <div v-if="user" role="alert">You are logged in!</div>
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
    // map `this.user` to `this.$store.getters.user`
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
</style>
