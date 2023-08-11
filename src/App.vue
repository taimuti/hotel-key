<template>
  <div class="login">
    <p class="login__logo">Hotel<span class="login__logo__color">Key</span></p>
      <form @submit="sendData" class="login__form">
        <input-data @passData="updateData" />
        <div class="login__chexkbox">
                <memorize-pass @change="memorizePass = !memorizePass" />
                <a href="#">Забыли пароль?</a>
        </div>
        <login-button />
      </form>
  </div>
</template>

<script>
import InputData from "./components/InputData.vue";
import MemorizePass from "./components/MemorizePass.vue";
import LoginButton from "./components/LoginButton.vue";

export default {
  name: 'App',

  components: {
    InputData,
    MemorizePass,
    LoginButton
  },

  data() {
    return {
        login: "",
        password: "",
        memorizePass: false,
        data: {},
    }
  },

  methods: {
    updateData(data) {
        this.login = data.login;
        this.password = data.password;
    },

    showPassword() {
        this.isShowed = !this.isShowed; 
        this.isShowed ? (document.getElementById('password').type = "text") : (document.getElementById('password').type = "password");
    },

    sendData() {
        alert("login: " + this.login + " password: " + this.password + " memorize password?: " + (this.memorizePass ? "yes" : "no"))
    }
  }
}
</script>

<style src="./style.css"></style>
