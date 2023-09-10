<template>
<div>
    <div class="login__input" :class="{login__input__focus : isFocusedLogin}">   
        <input
            @change="updateData"
            @focus="isFocusedLogin = true"
            @blur="isFocusedLogin = false"
            v-model="login"

            type="text"
            name="login"
            autocomplete="username"
            autocapitalize="none"
            tabindex="0"
            class="login__input__field"
            placeholder="Ваш логин" />
    </div>
</div>
</template>

<script>
export default {

    data() {
        return { 
            login: "",
            isFocusedLogin: false
        }
    },

    methods: {
        updateData() {
            this.$emit('passDataLogin', this.login);
        },
    }
}
</script>