<template>
    <header class="header" :style="{'padding-top' : headerMainHeight + 'px'}">
        <div class="header__fixed">
            <div class="header__main page-wrapper" ref="headerMain">
                <router-link to="/" class="header__logo">LOGOTYPE</router-link>
                <div :class="[{'burger-active' : burgerActive }, 'burger']" @click="burgerToCloseIcon">
                    <div class="burger__line"></div>
                    <div class="burger__line"></div>
                    <div class="burger__line"></div>
                </div>
            </div>
        </div>
        <transition name="menuShowAnimate">
            <div v-show="burgerActive" class="header__menu-wrapper" @click="burgerToCloseIcon">
                <div class="header__menu" :style="{'margin-top' : headerMainHeight + 'px'}" @click.stop>
                    <nav class="header__nav">
                        <router-link to="/about" class="nav__link">Меню</router-link>
                        <router-link to="/about" class="nav__link">Меню</router-link>
                        <router-link to="/about" class="nav__link">Меню</router-link>
                        <router-link to="/about" class="nav__link">Меню</router-link>
                        <router-link to="/about" class="nav__link">Меню</router-link>
                        <router-link to="/about" class="nav__link">Меню</router-link>
                    </nav>
                    <div class="header__authorization">
                        <router-link to="/about" class="auth__sing-in">Вход</router-link>
                        <router-link to="/about" class="auth__registration">Регистрация</router-link>
                    </div>
                    <router-link to="/about" class="row-1__text">Режим работы</router-link>
                    <router-link to="/about" class="row-1__text">Правила посещения</router-link>
                </div>
            </div>
        </transition>
    </header>
</template>

<script>
export default {
    name: 'default-header',
    data() {
        return {
            headerMainHeight: 0,
            burgerActive: false,
        }
    },
    methods: {
        getMainHeaderHeight() {
            this.headerMainHeight = this.$refs.headerMain.offsetHeight;
        },
        burgerToCloseIcon() {
            if (this.burgerActive) {
                this.burgerActive = false;
            } else {
                this.burgerActive = true;
            }
        },
    },
    mounted() {
        this.getMainHeaderHeight();
    }
}
</script>

<style scoped lang="scss">
    .header {
        &__main {
            background-color: #fff;
        }

        &__fixed {
            width: 100%;
            display: flex;
            flex-direction: column;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 3;
        }

        &__menu-wrapper {
            width: 100%;
            position: fixed;
            top: 0;
            bottom: 0;
            right: 0;
            z-index: 2;
        }

        &__menu {
            height: 100%;
            margin-left: auto;
            padding: 20px 30px;
            box-sizing: border-box;
            background-color: #fff;
            box-shadow: 0px 0px 30px #000000;
            @media (min-width: 480px) {
                max-width: 300px;
            }
            @media (max-width: 479px) {
                width: 100%;
            }
        }

        &__nav {
            margin-bottom: 95px;
            .nav {
                &__link {
                    display: block;
                    font-size: 16px;
                    text-align: center;
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
                        margin-bottom: 25px;
                    }
                }
            }
        }

        .row-1 {

            &__text {
                display: block;
                font-size: 14px;
                text-align: center;
                color: #000000;

                &:not(:last-child) {
                    margin-bottom: 10px;
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
        }

        &__logo {
            font-family: 'Montserrat';
            font-size: 20px;
            font-weight: bold;
            text-align: left;
            color: #000;
        }


        &__authorization {
            margin-bottom: 40px;
            .auth {
                &__registration,
                &__sing-in {
                    display: block;
                    font-size: 14px;
                    font-weight: 600;
                    text-align: center;
                    color: #000;
                }

                &__sing-in {
                    margin-bottom: 10px;
                }
            }
        }
    }

    .burger {
        width: 27px;
        height: 16px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        cursor: pointer;

        @media (min-width: 768px) {
            display: none;
        }

        &__line {
            width: 100%;
            height: 2px;
            background-color: #000;
            transition: 1s;
        }

        &-active {
            .burger__line {
                &:nth-child(1) {
                    transform: rotate(-45deg) translate(-5px, 9px);
                }

                &:nth-child(2) {
                    opacity: 0;
                }

                &:nth-child(3) {
                    transform: rotate(45deg) translate(-1px, -5px);
                }
            }
        }
    }

    .menuShowAnimate-enter-active {
        transition: all .5s ease-out;
    }

    .menuShowAnimate-leave-active {
        transition: all .5s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }

    .menuShowAnimate-enter-from,
    .menuShowAnimate-leave-to {
        transform: translateX(50px);
        opacity: 0;
    }
</style>