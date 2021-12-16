<template>
    <form class="subscribe-footer-form" @submit.prevent>
        <my-input-footer-email
        v-model:value.trim="email"
        :showInputError="showError"
        v-model:haveInputError="haveError"
        ></my-input-footer-email>
        <button class="subscribe-footer-form__btn" @click="postForm">Ok</button>
    </form>
</template>

<script>
export default {
    name: 'subscribe-footer-form',
    data() {
        return {
            email: '',
            showError: false,
            haveError: false
        }
    },
    methods: {
        postForm() {
            if (this.isValidly()) {
                console.log('goof')
            }
        },
        isValidly() {
            let result = false;
            if (this.haveError) {
                this.showError = true;
            } else {
                this.showError = false; 
                result = true;
            }

            return result;
        }
    }
}
</script>

<style scoped lang="scss">
    .subscribe-footer-form {
        max-width: 370px;
        width: 100%;
        display: flex;
        align-items: flex-start;
        

        &__btn {
            height: 30px;
            padding: 0 25px;
            margin-left: 10px;
            border-radius: 2px;
            background-color: #14A5DA;
            color: #fff;
        }
    }
</style>