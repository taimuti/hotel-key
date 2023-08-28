<template>
  <div class="login">
  
    <p class="login__logo">Hotel<span class="login__logo__color">Key</span></p>
    
    <form @submit="checkData" class="login__form">

      <input-data @passData="updateData" />

      <div v-if="isErrorLogin" class="login__input__error">Введите логин.</div>
      <div v-if="isErrorPass" class="login__input__error">Введите пароль.</div>

      <div class="login__chexkbox">
        
        <label tabindex="0">
          <input @change="memorizePass = !memorizePass" type="checkbox"/>
          Запомнить пароль
        </label>

        <a href="#" tabindex="0">Забыли пароль?</a>

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
      isErrorLogin: false,
      isErrorPass: false,
    };
  },

  methods: {
    updateData(data) {
      this.login = data.login;
      this.password = data.password;
    },

    checkData(event) {
      if (this.login == "" || this.password == "") {
        event.preventDefault();
        if (this.login) {this.isErrorLogin=false} else {
          this.isErrorLogin=true;
          return false
        }
        this.password ? this.isErrorPass=false : this.isErrorPass=true;
      } else {this.sendData()}
    },

    sendData() {
      alert(
        `login: ${this.login} password: ${this.password} memorize password?: ${this.memorizePass ? "yes" : "no"}`);
    },

  },
};
</script>

<style src="./style.css"></style>
