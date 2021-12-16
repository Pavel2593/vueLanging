<template>
    <div class="textarea__wrapper">
        <span
        v-if="lableText || postErrorText"
        :class="[{ 'textarea__lable-error': postErrorText }, 'textarea__lable']">
        {{(postErrorText) ? postErrorText : lableText}}
        </span>
        <textarea
        type="text"
        placeholder="Комментарии"
        v-bind="$attrs"
        :class="[{ 'textarea-error': postErrorText }, 'textarea']"
        :value="value"
        @input="updateTextarea"
        ></textarea>
    </div>
</template>

<script>
export default {
    name: 'my-textarea',
    props: {
        lableText: String,
        value: [String],
        postErrorText: String, 
    },
    methods: {
        updateTextarea(event) {
            this.$emit('update:value', event.target.value);
            this.$emit('update:postErrorText', '');
            this.resetError();
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
    .textarea {
        width: 100%;
        height: 128px;
        margin-bottom: 20px;
        padding: 14px 16px;
        border: 1px solid $colorBlue;
        border-radius: 2px;
        box-sizing: border-box;
        font-size: 10px;

        &-error {
            border-color: $colorError;
            &:focus {
                background-color: rgba($colorError, 0.1);   
            }
        }
        
        @media (min-width: 480px) {
            font-size: 14px;
        }

        &__wrapper {
            max-width: 570px;
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
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