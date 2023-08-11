<template>
<div @change="updateData"> 
    <div class="login__input">   
        <input
            v-model="userData.login"
            type="text"
            placeholder="Ваш логин"
            class="login__input__field"
            id="login"
            name="login"/>
    </div>
    <div class="login__input" @input="outlineDraw">
        <input
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
        }
    },

    methods: {
        updateData() {
            this.$emit('passData', this.userData);
        },
    },
}
</script>
