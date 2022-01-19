<template>
  <div class="register">
    <img src="../assets/rego.png" class="startup_image"/>
    <div class="register-information">
      <h1>Registration</h1>
      <span v-if="error" class="error">{{ error }}</span>
      <form @submit.prevent="Register">
        <label for="name">
          <input
            type="firstname"
            id="firstname"
            placeholder="Enter your firstname"
            v-model="firstname"
          />
        </label>
        <!--<label for="lastname">
          <input
            type="lastname"
            id="lastname"
            placeholder="Enter your lastname"
            v-model="lastname"
          />
        </label>-->
        <label for="email">
          <input
            type="email"
            id="email"
            placeholder="Enter your email"
            v-model="email"
          />
        </label>
        <label for="password">
          <input
            type="password"
            id="password"
            placeholder="Enter your password"
            v-model="password"
          />
        </label>
        <button value="Register" @click="submit">Create account</button>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase/compat/app';
import 'firebase/compat/auth';

export default {
  name: 'register',
  data() {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    submit() {
      console.log(this.email, this.password)
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then((data) => {
          data.user
            .updateProfile({
              displayName: this.firstname
            })
            .then(() => {
              alert('Successfully registered! Please login.');
              this.$router.replace('/login')
            })
        })
        .catch((err) => {
          this.error = err.message
        })
    }
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
.register img {
  position: absolute;
  top: 50%;
  left: 5%;
  transform: translate(0%, -50%);
  width: 30%;
}
.register-information {
  position: absolute;
  top: 50%;
  right: 5%;
  transform: translate(0%, -50%);
  width: 45%;
  padding: 6% 5% 5% 5%;
}
.register-information h1 {
  font-size: 58px;
  text-shadow: 2px 5px 6px #000000be;
  color: #ccc;
}
.register-information input {
  width: 70%;
  padding: 10px 0 10px 12px;
  outline: 0;
  background-color: transparent;
  border: 0;
  border-bottom: 1px solid #CCC;
  font-size: 17px;
}
.register-information input:focus {
  color: #333;
  transition: ease-in 0.3s;
  outline: none;
  background-color: #ecdbba23;
}
.register-information input::placeholder {
  color: #CCC;
}
.register form {
  margin-top: 24px;
}
label:nth-child(1),
label:nth-child(2),
label:nth-child(3) {
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
  background-color: #5AA897;
  color: black;
  border: 0px;
}
form button:after {
  content: '»';
  position: relative;
  opacity: 0;
}
form button:hover {
  background-color: #4f9687;
  transition: ease-in 0.2s;
  cursor: pointer;
}
form button:hover:after {
  opacity: 1;
  margin-left: 10px;
  transition: ease-in 0.2s;
}
@media screen and (max-width: 768px) {
  .register img {
    display: none;
  }
  .register-information {
    right: 0;
    width: 100%;
    padding: 0;
  }
  .register-information h1 {
    font-size: 56px;
  }
  .register-information input {
    font-size: 16px;
  }
  .register form {
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
