<template>
    <form @submit="checkData" class="login__form">
        <login-input @passLogin="updateLogin" @passPassword="updatePass"/>

        <div v-if="isErrorLogin" class="login__input__error">Введите логин.</div>
        <div v-if="isErrorPass" class="login__input__error">Введите пароль.</div>

        <login-checkbox @passData="updateFlagPass" />
        <login-button />
    </form>
</template>

<script>
import LoginInput from "./Input/LoginInput.vue";
import LoginCheckbox from "./LoginCheckbox.vue";
import LoginButton from "./LoginButton.vue";

export default {
    components: {
        LoginInput,
        LoginCheckbox,
        LoginButton,
    },
    data() {
        return {
            login: "",
            isErrorLogin: false,
            password: "",
            isErrorPass: false,
            memorizePass: false,
        };
    },
    methods: {
        updateLogin(value) {
            this.login = value;
        },
        updatePass(value) {
            this.password = value;
        },
        updateFlagPass(value) {
            this.memorizePass = value;
        },

        checkData(event) {
            if (this.login == "" || this.password == "") {
                event.preventDefault();
                if (this.login) {
                    this.isErrorLogin = false;
                } else {
                    this.isErrorLogin = true;
                    return false;
                }
                this.password ? (this.isErrorPass = false) : (this.isErrorPass = true);
            } else {
                this.sendData();
            }
        },

        sendData() {
            alert(`login: ${this.login} password: ${this.password} memorize password?: ${this.memorizePass ? "yes" : "no"}`);
        },
    },
};
</script>
