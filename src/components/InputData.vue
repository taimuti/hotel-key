<template>
<div> 
    <input-login @passDataLogin="updateDataLogin" />
    <input-pass @passDataPass="updateDataPass" />
</div>
</template>

<script>
import InputLogin from "./InputLogin.vue";
import InputPass from "./InputPass.vue";

export default {
    components: {
        InputLogin,
        InputPass
    },

    data() {
        return { 
            userData: {login: '', password: ''},
        }
    },

    methods: {
        updateDataLogin(data) {
            this.userData.login = data;
            this.$emit('passData', this.userData);
        },

        updateDataPass(data) {
            this.userData.password = data;
            this.$emit('passData', this.userData);
        }
    },
}
</script>
