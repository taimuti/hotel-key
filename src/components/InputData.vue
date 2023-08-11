<template>
<div @change="updateData"> 
    <div class="login__input" :class="{login__input__focus : isFocusedLogin}">   
        <input
            @focus="isFocusedLogin = true"
            @blur="isFocusedLogin = false"
            v-model="userData.login"
            type="text"
            placeholder="Ваш логин"
            class="login__input__field"
            id="login"
            name="login"/>
    </div>
    <div class="login__input" :class="{login__input__focus : isFocusedPass}">
        <input
            @focus="isFocusedPass = true"
            @blur="isFocusedPass = false"
            v-model="userData.password"
            type="password"
            placeholder="Ваш пароль"
            class="login__input__field"
            id="password"
            name="password"/>
        <show-pass-button />
    </div>
</div>
</template>

<script>
import ShowPassButton from "./ShowPassButton.vue";

export default {
    components: {
        ShowPassButton
    },

    data() {
        return { 
            userData: {login: '', password: ''},
            isShowed: false,
            isFocusedLogin: false,
            isFocusedPass: false,
        }
    },

    methods: {
        updateData() {
            this.$emit('passData', this.userData);
        },

        focusLogin() {
            this.isFocusedLogin = false;
        },

        outlineDivPass() {

        },

        outlineNone() {
            document.getElementById("login-div").style = 'none'
        }
    },
}
</script>
