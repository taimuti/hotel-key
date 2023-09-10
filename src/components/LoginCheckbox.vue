<template>
    <div class="login__chexkbox">
        <label tabindex="0">
            <input @change="updateData" type="checkbox" />
            Запомнить пароль
        </label>

        <a href="#" tabindex="0">Забыли пароль?</a>
    </div>
</template>

<script>
export default {
    data() {
        return {
            memorizePass: false,
        };
    },

    methods: {
        updateData() {
            this.memorizePass = !(this.memorizePass);
            this.$emit('passData', this.memorizePass);
        },
    }
}
</script>