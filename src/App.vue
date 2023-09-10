<template>
  <div class="login">
    <p class="login__logo">Hotel<span class="login__logo__color">Key</span></p>
    <login-form />
  </div>
</template>

<script>
import LoginForm from "./components/LoginForm.vue";

export default {
  name: "App",

  components: {
    LoginForm
  },
};
</script>

<style src="./style.css"></style>
