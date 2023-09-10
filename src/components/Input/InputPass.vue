<template>
    <div class="login__input" :class="{login__input__focus : isFocusedPass}">
        <input
            @change="updateData"
            @focus="isFocusedPass = true"
            @blur="isFocusedPass = false"
            v-model="password"
            ref="password"
            
            type="password"
            name="password"
            autocomplete="current-password"
            autocapitalize="none"
            tabindex="0"
            class="login__input__field"
            placeholder="Ваш пароль"/>
        <show-pass-button @showPassword="updateType"/>
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
            password: "",
            isFocusedPass: false,
        }
    },

    methods: {
        updateData() {
            this.$emit('passDataPass', this.password);
        },

        updateType(val) {
            this.$refs.password.type = val;
        }
    },
}
</script>
