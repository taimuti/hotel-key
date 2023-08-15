<template>
  <div class="login">
    <p class="login__logo">Hotel<span class="login__logo__color">Key</span></p>
    <form @submit="sendData" class="login__form">
      <input-data @passData="updateData" />
      <div class="login__chexkbox">
        <label>
          <input type="checkbox" @change="memorizePass = !memorizePass" />
          Запомнить пароль
        </label>
        <a href="#">Забыли пароль?</a>
      </div>
      <login-button />
    </form>
  </div>
</template>

<script>
import InputData from "./components/InputData.vue";
import LoginButton from "./components/LoginButton.vue";

export default {
  name: "App",

  components: {
    InputData,
    LoginButton,
  },

  data() {
    return {
      login: "",
      password: "",
      memorizePass: false,
    };
  },

  methods: {
    updateData(data) {
      this.login = data.login;
      this.password = data.password;
    },

    sendData() {
      alert(
        `login: ${this.login} password: ${this.password} memorize password?: ${this.memorizePass ? "yes" : "no"}`);
    },
  },
};
</script>

<style src="./style.css"></style>
