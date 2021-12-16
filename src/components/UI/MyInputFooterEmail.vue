<template>
    <div class="input__wrapper">
        <input
        type="text"
        placeholder="example@mail.ru"
        class="input"
        :value="value"
        @input="updateInput"
        >
        <span
        class="input__lable"
        v-if="showInputError && error.text != ''">
        {{error.text}}
        </span>
    </div>
</template>

<script>
export default {
    name: 'my-input-footer-email',
    data() {
        return {
            error: {
                enabled: false,
                text: ''
            }
        }
    },
    props: {
        lableText: String,
        value: String,
        showInputError: Boolean,
        haveInputError: Boolean,
    },
    methods: {
        updateInput(event) {
            this.$emit('update:value', event.target.value);
            this.validationEmail(event.target.value);
            this.$emit('update:haveInputError', this.error.enabled);
        },
        validationEmail(value) {
            const regex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            if (regex.test(value)) {
                this.error.enabled = false;
                this.error.text = '';
            } else {
                this.error.enabled = true;
                this.error.text = 'Email не корректный';
            }
        }
    }
}
</script>

<style scoped lang="scss">
    .input {
        width: 100%;
        height: 30px;
        padding: 0 16px;
        border-radius: 2px;
        box-sizing: border-box;
        font-size: 12px;

        &__wrapper {
            max-width: 290px;
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
        }

        &__lable {
            margin-top: 10px;
            padding-left: 16px;
            font-size: 14px;
            text-align: left;
            color: #000;
        }
    }
</style>