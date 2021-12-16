<template>
    <footer class="default-footer">
        <div class="page-wrapper">
            <router-link to="/" class="default-footer__logo">LOGOTYPE</router-link>
            <div class="default-footer__row">
                <div class="default-footer__col-1">
                    <a href="https://yandex.ru/maps/213/moscow/house/baumanskaya_ulitsa_44s1/Z04YcABoTkAAQFtvfXt2cXlmbA==/?ll=37.669460%2C55.763563&z=14"
                    target="_blank"
                    class="default-footer__address default-footer__text">г. Москва, метро Бауманская, ул. Бауманская, дом 44</a>
                    <a href="tel:+7 000 000 00 00" class="default-footer__phone-number default-footer__text">+7 000 000 00 00</a>
                </div>
                <div class="default-footer__col-2">
                    <nav class="footer-nav">
                        <div class="footer-nav__wrapper">
                            <router-link to="/about" class="footer-nav__link">О компании</router-link>
                            <router-link to="/about" class="footer-nav__link">Партнёрская программа</router-link>
                            <router-link to="/about" class="footer-nav__link">Реклама</router-link>
                            <router-link to="/about" class="footer-nav__link">Пресс-центр</router-link>
                            <router-link to="/about" class="footer-nav__link">Вакансии</router-link>
                            <router-link to="/about" class="footer-nav__link">Помощь</router-link>
                            <router-link to="/about" class="footer-nav__link">Правила</router-link>
                        </div>
                    </nav>
                    <div class="default-footer__social">
                        <div class="social">
                            <div class="social__title">Мы в соц. сетях</div>
                            <div class="social__list">
                                <a href="#" class="social__link">
                                    <svg width="11" height="25">
                                        <use href="./../assets/icons.svg#facebook"></use>
                                    </svg>
                                </a>
                                <a href="#" class="social__link">
                                    <svg width="18" height="25">
                                        <use href="./../assets/icons.svg#odnoklassniki"></use>
                                    </svg>
                                </a>
                                <a href="#" class="social__link">
                                    <svg width="25" height="25">
                                        <use href="./../assets/icons.svg#instagram"></use>
                                    </svg>
                                </a>
                            </div>
                        </div>
                        <div class="subscribe-footer-form__wrapper">
                            <span class="subscribe-footer-form__title default-footer__text">Подписка на новости</span>
                            <SubscribeFooterForm/>
                        </div>
                    </div>
                </div>  
            </div>
        </div>
    </footer>
    <div class="default-footer__background">
        <div class="page-wrapper default-footer__row-2">
            <router-link to="/about" class="default-footer__copyright">© ООО «Глобус», 2016 — 2019</router-link>
            <div class="default-footer__box">
                <router-link to="/about" class="default-footer__privacy-policy">Политика конфиденциальности</router-link>
                <router-link to="/about" class="default-footer__cookies">Cookies</router-link>
            </div>
        </div>
    </div>
</template>

<script>
import SubscribeFooterForm from '@/components/SubscribeFooterForm.vue'
export default {
    name: 'default-footer',
    components: {
        SubscribeFooterForm,
    }
}
</script>

<style lang="scss">
    .default-footer {
        padding: 30px 0;
        background-color: #DCE5E9;

        &__text {
            display: block;
            font-family: 'Montserrat';
            font-size: 14px;
            color: #000;
        }

        &__row {
            display: flex;
            justify-content: space-between;
            @media (max-width: 767px) {
                flex-direction: column;
                align-items: center;
            }
        }

        &__col-1 {
            max-width: 215px;
            // margin-right: 30px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        &__logo {
            margin-bottom: 20px;
            display: block;
            font-family: 'Montserrat';
            font-size: 20px;
            font-weight: bold;
            text-align: left;
            color: #000;
            @media (max-width: 767px) {
                margin-bottom: 10px;
                text-align: center;
            }
        }

        &__address {
            margin-bottom: 60px;
            text-align: left;
            line-height: 1.3;
            @media (max-width: 767px) {
                margin-bottom: 20px;
                text-align: center;
            }
        }

        &__phone-number {
            font-weight: bold;
            text-align: left;
            @media (max-width: 767px) {
                margin-bottom: 25px;
                text-align: center;
            }
        }

        &__col-2 {
            @media (max-width:1199px) {
                display: flex;
                flex-grow: 2;
            }
            @media (max-width: 767px) {
                width: 100%;
                flex-direction: column;
            }
        }

        .footer-nav {
            margin-bottom: 35px;
            @media (max-width:1199px) {
                margin-bottom: 0;
                display: flex;
                justify-content: center;
                flex-grow: 2;
            }
            @media (max-width: 767px) {
                margin-bottom: 25px;
            }

            &__wrapper {
                display: flex;
                @media (max-width:1199px) {
                    flex-direction: column;
                }
            }

            &__link {
                font-size: 14px;
                text-align: left;
                color: #000;

                &:not(:last-child) {
                    margin-right: 24px;
                    @media (max-width:1199px) {
                        margin-right: 0;
                    }
                }

                @media (max-width: 767px) {
                    text-align: center;
                }

                @media (max-width: 1199px) {
                    margin-bottom: 8px;
                }
            }
        }

        &__social {
            display: flex;
            justify-content: space-between;
            @media (max-width: 1199px) {
                flex-direction: column;
            }
            @media (max-width:767px) {
                align-items: center;
            }
        }

        .social {
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            align-items: flex-start;
            @media (max-width: 767px) {
                align-items: center;
            }

            &__title {
                margin-bottom: 17px;
                font-family: 'Montserrat';
                font-size: 14px;
                white-space: nowrap;
                color: #000;
                @media (max-width: 767px) {
                    margin-bottom: 20px;
                }
            }

            &__list {
                display: flex;
                justify-content: center;
                @media (max-width:767px) {
                    margin-bottom: 40px;
                }
            }

            &__link {
                &:not(:last-child) {
                    margin-right: 12px;
                    @media (max-width:767px) {
                        margin-right: 20px;
                    }
                }

                & svg {
                    height: 15px;
                    fill: #14a5da;
                    @media (max-width:767px) {
                        height: 25px;
                    }
                }
            }
        }

        .subscribe-footer-form {
            &__wrapper {
                @media (max-width:767px) {
                    width: 100%;
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                }
            }

            &__title {
                margin-bottom: 10px;
                text-align: left;
                @media (max-width:767px) {
                    height: 25px;
                }
            }
        }

        &__background {
            background-color: #001F2B;
        }

        &__row-2 {
            padding: {
                top: 25px;
                bottom: 25px;
            }
            display: flex;
            justify-content: space-between;
            align-items: center;
            @media (max-width:767px) {
                flex-direction: column-reverse;
            }
        }

        &__box {
            @media (max-width:768px) {
                width: 100%;
                margin-bottom: 30px;
                display: flex;
                justify-content: space-between;
            }
        }

        &__copyright,
        &__privacy-policy,
        &__cookies {
            font-size: 12px;
            color: #DCE5E9;
        }

        &__privacy-policy {
            margin-right: 30px;
        }

    }

</style>