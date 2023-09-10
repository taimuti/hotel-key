<template>
    <form @submit="checkData" class="login__form">
        <input-data @passData="updateData" />

        <div v-if="isErrorLogin" class="login__input__error">Введите логин.</div>
        <div v-if="isErrorPass" class="login__input__error">Введите пароль.</div>

        <login-checkbox @passData="updateFlagPass" />
        <login-button />
    </form>
</template>

<script>
import InputData from "./Input/InputData.vue";
import LoginCheckbox from "./LoginCheckbox.vue";
import LoginButton from "./LoginButton.vue";

export default {
    components: {
        InputData,
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
        updateData(data) {
            this.login = data.login;
            this.password = data.password;
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
