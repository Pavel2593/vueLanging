<template>
    <header class="header">
        <div class="header__row-1" ref="headerRow1" :style="(headerSlick) ? {'margin-bottom' : headerMainHeight + 'px'} : {}">
            <div class="row-1__wrapper page-wrapper">
                <router-link to="/about" class="row-1__text">Режим работы</router-link>
                <router-link to="/about" class="row-1__text">Правила посещения</router-link>
            </div>
        </div>
        <div :class="{'header__main-fixed' : headerSlick}">
            <div class="header__main page-wrapper" ref="headerMain">
                <router-link to="/" class="header__logo">LOGOTYPE</router-link>
                <nav class="header__nav">
                    <router-link to="/about" class="nav__link">Меню</router-link>
                    <router-link to="/about" class="nav__link">Меню</router-link>
                    <router-link to="/about" class="nav__link">Меню</router-link>
                    <router-link to="/about" class="nav__link">Меню</router-link>
                    <router-link to="/about" class="nav__link">Меню</router-link>
                    <router-link to="/about" class="nav__link">Меню</router-link>
                </nav>
                <div class="header__authorization">
                    <router-link to="/about" class="auth__registration">Регистрация</router-link>
                    <router-link to="/about" class="auth__sing-in">Вход</router-link>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'defaultesktop-header',
    data() {
        return {
            headerSlick: false,
            headerMainHeight: 0,
        }
    },
    methods: {
        handlerScroll() {
            this.headerMainHeight = this.$refs.headerMain.offsetHeight;
            const headerRow1Height = this.$refs.headerRow1.offsetHeight;
            const scrollHeight =  window.pageYOffset;
            if (headerRow1Height < scrollHeight) {
                this.headerSlick = true;
            } else {
                this.headerSlick = false;
            }
        },
    },
    created() {
        window.addEventListener('scroll', this.handlerScroll);
    },
    destroyed() {
        window.removeEventListener('scroll', this.handlerScroll);
    },
}
</script>

<style scoped lang="scss">
    .header {
        &__row-1 {
            background-color: #BBBBBB;
        }

        .row-1 {
            &__wrapper {
                padding: {
                    top: 11px;
                    bottom: 11px;
                };
                display: flex;
                justify-content: space-between;
            }

            &__text {
                font-size: 14px;
                color: #000000;

                &:not(:last-child) {
                    @media (max-width:767px) {
                        // margin-bottom: 10px;
                    }
                }
            }
        }

        &__main {
            padding: {
                top: 45px;
                bottom: 30px;
            };
            display: flex;
            justify-content: space-between;
            align-items: center;

            @media (max-width: 1199px) {
                flex-wrap: wrap;
            }

            @media (max-width: 1024px) {
                padding: {
                    top: 20px;
                    bottom: 20px;
                };
            }

            &-fixed {
                width: 100%;
                position: fixed;
                top: 0;
                left: 0;
                background-color: #fff;
                z-index: 2;
            }
        }

        &__logo {
            font-family: 'Montserrat';
            font-size: 20px;
            font-weight: bold;
            text-align: left;
            color: #000;
        }

        &__nav {
            display: flex;
            justify-content: center;
            @media (max-width: 1199px) {
                width: 100%;
                margin-top: 30px;
                order: 1;
            }

            .nav {
                &__link {
                    font-size: 16px;
                    color: #000;

                    &:after {
                        content: "";
                        display: block;
                        width: 0%;
                        height: 2px;
                        background-color: #000;
                        -webkit-transition: width .3s ease-in-out;
                        -moz--transition: width .3s ease-in-out;
                        transition: width .3s ease-in-out;
                    }

                    &:hover:after {
                        width: 100%;
                    }

                    &:hover {
                        font-weight: bold;
                    }

                    &:not(:last-child) {
                        margin-right: 60px;
                    }
                }
            }
        }

        &__authorization {
            .auth {
                &__registration,
                &__sing-in {
                    font-size: 12px;
                    font-weight: 600;
                    color: #000;
                }

                &__registration {
                    margin-right: 25px;
                }
            }
        }
    }
</style>