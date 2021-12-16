<template>
    <section class="page-wrapper">
        <div class="position-relative">
            <div v-if="submitForm" class="subscribe-form__submit">
                <svg width="61" height="61" class="submit__svg">
                    <use href="./../assets/icons.svg#checkGreen"></use>
                </svg>
                <div class="submit__text">Уважаемый, {{user.name}}, спасибо за подписку!</div>
            </div>
            <form class="subscribe-form" @submit.prevent>
                <svg width="21" height="21" class="subscribe-form__logo">
                    <use href="./../assets/icons.svg#wifiLogo"></use>
                </svg>
                <h3 class="subscribe-form__title">подпишитесь на рассылку</h3>
                <div class="subscribe-form__first-row">
                    <my-input-name v-model:value.trim="user.name" v-model:postErrorText="error.name" :lableText="'Имя'"></my-input-name>
                    <my-input-email v-model:value.trim="user.email" v-model:postErrorText="error.email"></my-input-email>
                </div>
                <my-textarea v-model:value.trim="user.text" v-model:postErrorText="error.text"></my-textarea>
                <button @click="postForm" class="subscribe-form__btn">Подписаться</button>
            </form>
        </div>
    </section>
</template>

<script>
export default {
    name: 'SubscribeForm',
    data() {
        return {
            submitForm: false,
            user: {
                name: '',
                email: '',
                text: ''
            },
            error: {
                name: '',
                email: '',
                text: ''
            }
        }
    },
    methods: {
        postForm() {
            //Здесь отправляем форму ajax на back
            if (this.isValidly()) {
                this.submitForm = true;
            }
        },
        isValidly() {
            let result = true;
            const obj = this.user;
            for (var key in obj) {
                this.error[key] = this.checkEmpty(obj[key], this.error[key]);
                if (this.error[key] != '') {
                    result = false;
                }
            }
            return result;
        },
        checkEmpty(str, error) {
            let result = '';
            if (str == '') {
                result = 'Заполните поле';
            } else {
                result = error
            }
            return result;
        }
    }
}
</script>

<style lang="scss">
    .subscribe-form {
        $colorBlue: #14A5DA;
        margin-bottom: 40px;
        padding: 30px 35px 35px;
        border: 1px solid $colorBlue;
        display: flex;
        flex-direction: column;
        align-items: center;
        position: relative;

        &::after {
            content: ''; 
            position: absolute; 
            top: 0; 
            left: 0;
            border: 39px solid transparent;
            border-left: 39px solid rgba($colorBlue, 0.1);
            border-top: 39px solid rgba($colorBlue, 0.1);

            @media (max-width:767px) {
                border: 24px solid transparent;
                border-left: 24px solid rgba($colorBlue, 0.1);
                border-top: 24px solid rgba($colorBlue, 0.1);
            }
        }

        @media (min-width:1024px) {
            margin-bottom: 60px;
            padding: 40px 35px 35px;
        }

        &__submit {
            width: 100%;
            height: 100%;
            padding: 0 15px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: absolute;
            top: 0;
            left: 0;
            background-color: #fff;
            box-shadow: 0px 0px 10px #00000029;
            z-index: 1;

            .submit {
                &__svg {
                    fill: #3dcc89;
                    margin-bottom: 25px;
                    @media (max-width:767px) {
                        width: 40px;
                        height: 40px;
                    }
                }

                &__text {
                    font-family: "Montserrat";
                    font-size: 20px;
                    font-weight: 600;
                    text-transform: uppercase;
                    text-align: center;
                    @media (max-width:767px) {
                        font-size: 12px;
                    }
                }
            }
        }

        &__logo {
            fill: $colorBlue;
            position: absolute;
            top: 10px;
            left: 10px;

            @media (max-width:767px) {
                width: 12px;
                height: 12px;
                top: 7px;
                left: 7px;
            }
        }

        &__title {
            margin-bottom: 25px;
            font-weight: 600;
            text-transform: uppercase;
        }

        &__first-row {
            max-width: 570px;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
            @media (max-width: 767px) {
                flex-direction: column;
                align-items: center;
            }
        }

        &__btn {
            max-width: 270px;
            width: 100%;
            height: 40px;
            border-radius: 2px;
            font-size: 10px;
            text-transform: uppercase;
            background-color: $colorBlue;
            color: #fff;
            @media (min-width:480px) {
               font-size: 14px; 
            }
        }
    }
</style>