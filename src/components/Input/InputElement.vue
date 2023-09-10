<template>
    <div class="login__input" :class="{login__input__focus : isFocused}">
        <input 
            :value="modelValue"
            :type="type"
            @input="$emit('update:modelValue', $event.target.value)"
            v-bind="$attrs"

            ref="input"
            @focus="isFocused = true"
            @blur="isFocused = false"
           
            autocapitalize="none"
            tabindex="0"
            class="login__input__field">
        <input-show-button v-if="type=='password'" @showPassword="updateType"/>
    </div>
</template>

<script>
import InputShowButton from "./InputShowButton.vue";

export default {
    components: {
        InputShowButton
    },

    props: {
        modelValue: {
            type: String,
            default: ""
        },
        type: {
            type: String,
            default: "text"
        }
    },

    data() {
        return { 
            isFocused: false
        }
    },

    methods: {
        updateType(val) {
            this.$refs.input.type = val;
        }
    },
}
</script>