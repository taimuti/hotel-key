<template>
<div> 
    <div class="login__input" :class="{login__input__focus : isFocusedLogin}">   
        <input
            @change="updateData"
            @focus="isFocusedLogin = true"
            @blur="isFocusedLogin = false"
            v-model="userData.login"
            type="text"
            placeholder="Ваш логин"
            class="login__input__field"
            name="login"/>
    </div>
    <div class="login__input" :class="{login__input__focus : isFocusedPass}">
        <input
            @change="updateData"
            @focus="isFocusedPass = true"
            @blur="isFocusedPass = false"
            v-model="userData.password"
            ref="password"
            type="password"
            placeholder="Ваш пароль"
            class="login__input__field"
            name="password"/>
        <show-pass-button 
            @showPassword="updateType"/>
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
            isFocusedLogin: false,
            isFocusedPass: false,
        }
    },

    methods: {
        updateData() {
            this.$emit('passData', this.userData);
        },

        updateType(val) {
            console.log(val)
            this.$refs.password.type = val;
        }
    },
}
</script>
