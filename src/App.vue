<template>
  <div class="login">
        <p class="login__logo">Hotel<span class="login__logo__color">Key</span></p>
        <form @submit="sendData" class="login__form">
            <InputData @passData="updateData" />
            <div class="login__chexkbox">
                <MemorizePass @change="memorizePass = !memorizePass" />
                <a href="#">Забыли пароль?</a>
            </div>
            <button type="submit" class="login__button">Войти в аккаунт</button>
        </form>
    </div>
</template>

<script>
import InputData from "./components/InputData.vue";
import MemorizePass from "./components/MemorizePass.vue";

export default {
  name: 'App',

  components: {
    InputData,
    MemorizePass
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
