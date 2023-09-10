<template>
<div>
    <input-element 
        v-model="login"
        name="login"
        autocomplete="username"
        placeholder="Ваш логин" />
    <input-element 
        v-model="password"
        type="password"
        name="password"
        autocomplete="current-password"
        placeholder="Ваш пароль" />
</div>
</template>

<script>
import InputElement from "./InputElement.vue";

export default {
    components: {
        InputElement
    },

    data() {
        return { 
            login: "",
            password: "",
        }
    },

    watch: {
        login(newValue) {
            this.$emit('passLogin', newValue);
        },
        password(newValue) {
            this.$emit('passPassword', newValue);
        }
    },
}
</script>
