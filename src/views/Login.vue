<template>
  <div class="login">
    <img src="../assets/rego.png" class="startup_image"/>
    <div class="login-information">
      <h1>Login</h1>
      <form @submit.prevent="submit">
        <label for="email">
          <input
            type="email"
            id="email"
            placeholder="enter your email"
            v-model="email"
          />
        </label>
        <label for="password">
          <input
            type="password"
            id="password"
            placeholder="enter your password"
            v-model="password"
          />
        </label>
        <button value="Login" @click="login">LOGIN</button>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase/compat/app'
import 'firebase/compat/auth'

export default {
  name: 'login',
  data() {
    return {
      firstname: '',
      lastname: '',
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login() {
    firebase
      .auth()
      .signInWithEmailAndPassword(this.email, this.password)
      .then(() => {
        alert('Successfully logged in');
        this.$router.push('/dashboard');
      })
      .catch(error => {
        alert(error.message);
      });
  },
  },
}
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
body {
  height: 100vh;
}
.login img {
  position: absolute;
  top: 50%;
  left: 5%;
  transform: translate(0%, -50%);
  width: 35%;
}
.login-information {
  position: absolute;
  top: 50%;
  right: 5%;
  transform: translate(0%, -50%);
  width: 45%;
  padding: 6% 5% 5% 5%;
}
.login-information h1 {
  font-size: 58px;
  text-shadow: 2px 3px 6px #000000be;
  color: #ccc;
}
.login-information input {
  width: 70%;
  padding: 10px 0 10px 12px;
  outline: 0;
  background-color: transparent;
  border: 0;
  border-bottom: 1px solid #CCC;
  font-size: 17px;
}
.login-information input:focus {
  color: #333;
  transition: ease-in 0.3s;
  outline: none;
  background-color: #ecdbba23;
}
.login-information input::placeholder {
  color: #CCC;
}
.login form {
  margin-top: 24px;
}
label:nth-child(1),
label:nth-child(2) {
  display: block;
  width: 100%;
  margin: 0 auto;
  padding-bottom: 20px;
}
form button {
  width: 240px;
  font-size: 17px;
  padding: 12px 0;
  border-radius: 8px;
  margin-top: 12px;
  background-color: #199a84;
  color: black;
  border: 0px;
}
form button:after {
  content: '»';
  position: relative;
  opacity: 0;
}
form button:hover {
  background-color: #158471;
  transition: ease-in 0.2s;
  cursor: pointer;
}
form button:hover:after {
  opacity: 1;
  margin-left: 10px;
  transition: ease-in 0.2s;
}
@media screen and (max-width: 768px) {
  .login img {
    display: none;
  }
  .login-information {
    right: 0;
    width: 100%;
    padding: 0;
  }
  .login-information h1 {
    font-size: 56px;
  }
  .login-information input {
    font-size: 16px;
  }
  .login form {
    margin-top: 36px;
  }
  form button {
    width: 180px;
    font-size: 16px;
    padding: 10px 0;
  }
  form button:hover {
    transition: ease-in 0.1s;
  }
  form button:hover:after {
    margin-left: 10px;
    transition: ease-in 0.1s;
  }
}
</style>
