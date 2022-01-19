<template>
  <div class="contact">
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

    <h1>You have questions for us?</h1>
    <h2>Get in touch with us!</h2>
    <form @submit.prevent="sendEmail">
      <!--<label>Name</label>-->
      <input
        type="text"
        v-model="name"
        name="name"
        placeholder="Your Name"
      >
      <!--<label>Email</label>-->
      <input
        type="email"
        v-model="email"
        name="email"
        placeholder="Your Email"
      >
      <!--<label>Message</label>-->
      <textarea
        name="message"
        v-model="message"
        rows="8"
        placeholder="Message">
      </textarea>

      <input type="submit" value="Send">
    </form>
    <div class="info">
      <i class="far fa-map"><p>Radnička cesta 47, Zagreb, Hrvatska</p></i>
      <i class="fas fa-phone-alt"><p>+385 91 732 4270</p></i>
      <i class="fas fa-clock"><p><b>Mon-Fri</b> : 09:00-17:00</p></i>
    </div>
  </div>
</template>

<style scoped>
</style>

<script>
import emailjs from 'emailjs-com';

export default {
  name: 'ContactForm',
  data() {
    return {
      hamburgerOpen: false,
      name: '',
      email: '',
      message: ''
    }
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('service_021yx7l', 'template_28jr628', e.target,
        'user_Z8v3GL7mhuHQbwmfi4RhV', {
          name: this.name,
          email: this.email,
          message: this.message
        })

      } catch(error) {
          console.log({error})
      }
      // Reset form field
      this.name = ''
      this.email = ''
      this.message = ''
    },
  }
}
</script>

<style scoped>
.contact {
  width: 100%;
  position: absolute;
  top: 44%;
  right: 50%;
  transform: translate(50%, -50%);
}
h1 {
  text-align: left;
  margin-left: 8%;
  font-size: 48px;
  color: #333;
  padding-top: 80px;
}
h2 {
  text-align: left;
  margin-left: 8%;
  font-size: 28px;
  color: #333;
}
form {
  width: 30%;
  margin-left: 8%;
  margin-top: 50px;
  display: block;
  text-align: center;
  padding: 20px;
}
input[type=text], [type=email], textarea {
  width: 100%;
  font-size: 16px;
  padding: 12px 0 12px 16px;
  border: 1px solid #333;
  border-radius: 6px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}
input[type=submit] {
  width: 100%;
  font-size: 16px;
  background-color: #4CAF50;
  color: white;
  padding: 12px 0px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
input[type=submit]:hover {
  background-color: #45A049;
}
input:focus, textarea:focus {
  outline: 0;
}
.info {
  position: absolute;
  top: 270px;
  left: 45%;
  width: 600px;
  height: 432px;
  float: right;
  margin-right: 8%;
  padding: 110px 0;
  border-left: 4px solid #333;
}
.info i {
  float: left;
  font-size: 26px;
  font-weight: bold;
  padding-left: 120px;
  margin-bottom: 50px;
}
.info p {
  float: right;
  font-size: 22px;
  font-weight: 400;
  padding-left: 24px;
  margin-top: 2px;
}
@media screen and (max-width: 1280px) {
  h1 {
    margin-left: 7%;
    padding-top: 120px;
  }
}
@media screen and (max-width: 1080px) {
  .contact {
    top: 0;
    right: 0;
    transform: translate(0%, 0%);
  }
  h1 {
    text-align: center;
    margin-left: 0;
    font-size: 48px;
    margin-top: 30px;
  }
  h2 {
    text-align: center;
    font-size: 28px;
  }
  form {
    width: 60%;
    margin-left: 20%;
    margin-top: 380px;
    padding: 0;
  }
  input[type=submit] {
    margin-bottom: 40px;
  }
  .info {
    top: 240px;
    left: 22%;
    width: 56%;
    height: 350px;
    float: none;
    margin-right: 0;
    border: 0;
  }
  .info i {
    display: block;
    font-size: 32px;
    padding: 0 35px 0 0;
    margin-bottom: 50px;
  }
}
@media screen and (max-width: 900px) {
  .info {
    left: 15%;
    width: 70%;
  }
  .info i {
    padding: 0 50px 0 0;
  }
}
@media screen and (max-width: 768px) {
  h1 {
    font-size: 48px;
    margin-top: 100px;
    padding: 0;
  }
  h2 {
    text-align: center;
    font-size: 28px;
    font-weight: 400;
  }
  .info {
    top: 220px;
    left: 6%;
    width: 94%;
    height: 350px;
  }
  .info i {
    display: block;
    font-size: 32px;
    padding: 0 70px 0 0;
    margin-bottom: 50px;
  }
}
@media screen and (max-width: 600px) {
  h1 {
    font-size: 40px;
  }
  h2 {
    text-align: center;
    font-size: 24px;
    padding-top: 5px;
  }
  form {
    width: 86%;
    margin-left: 7%;
    margin-top: 500px;
  }
  input[type=text], [type=email], textarea {
    font-size: 15px;
    padding: 10px 0 10px 15px;
    margin-top: 12px;
    margin-bottom: 20px;
  }
  .info {
    top: 260px;
    left: 0;
    width: 100%;
    text-align: center;
  }
  .info i {
    float: none;
    font-size: 21px;
    padding: 0;
    margin-bottom: 60px;
  }
  .info p {
    float: none;
    font-size: 19px;
    padding-left: 0px;
    margin-top: 15px;
  }
}

</style>
