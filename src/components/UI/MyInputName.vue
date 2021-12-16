<template>
    <div class="input__wrapper">
        <span
        v-if="lableText || postErrorText"
        :class="[{ 'input__lable-error': postErrorText }, 'input__lable']">
        {{(postErrorText) ? postErrorText : lableText}}
        </span>
        <input
        type="text"
        v-bind="$attrs"
        :class="[{ 'input-error': postErrorText }, 'input']"
        :value="value"
        @input="updateInput"
        >
    </div>
</template>

<script>
export default {
    name: 'my-input-name',
    inheritAttrs: false,
    data() {
    },
    props: {
        lableText: String,
        value: [String, Number],
        postErrorText: String, 
    },
    methods: {
        updateInput(event) {
            this.$emit('update:value', event.target.value);
            this.resetError();
            this.checkNumber(event.target.value);
            this.$emit('update:postErrorText', this.error.text);
        },
        checkNumber(value) {
            const regex = /[0-9]/;
            let error = {
                enabled: false,
                text: ''
            }
            if (regex.test(value)) {
                error.enabled = true;
                error.text = 'Цифры в имени не допустимы';
            } else {
                error.enabled = false;
                error.text = '';
            }
            this.error = error;
        },
        resetError() {
            const resetError = {
                enabled: false,
                text: ''
            }
            this.error = resetError;
        }
    },
}
</script>

<style scoped lang="scss">
    $colorBlue: #14A5DA;
    $colorError: #E76400;
    .input {
        width: 100%;
        height: 32px;
        margin-bottom: 20px;
        padding: 0 16px;
        border: 1px solid $colorBlue;
        border-radius: 2px;
        box-sizing: border-box;
        font-size: 10px;

        &:focus {
            background-color: rgba($colorBlue, 0.1);   
        }

        @media (min-width: 480px) {
            height: 40px;
            margin-bottom: 25px;
            font-size: 14px;
        }

        &-error {
            border-color: $colorError;
            &:focus {
                background-color: rgba($colorError, 0.1);   
            }
        }

        &__wrapper {
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            @media (min-width: 768px) {
                max-width: 270px;
            }
        }

        &__lable {
            margin-bottom: 5px;
            padding-left: 16px;
            font-size: 8px;
            text-align: left;

            @media (min-width: 480px) {
                font-size: 12px;
            }

            &-error {
                color: $colorError
            }
        }
    }
</style>