<template>
<!-- :autoplay="true" -->
    <VueAgile class="banner-slider__wrapper" :arrows="true" :dots="true" >
        <router-link to="/about" class="banner-slider__item" v-for="item in bannerItem" :key="item.id">
            <img class="banner-slider__banner"
            :src="item.src"
            :srcset="item.srcRetina+' 2x'"
            alt="background">
            <div class="banner-slider__item-filter">
                <div class="page-wrapper">
                    <button class="banner-slider__btn">{{item.buttom}}</button>
                    <span class="banner-slider__title">{{item.title}}</span>
                    <p class="banner-slider__text">{{item.text}}</p>
                </div>
            </div>
        </router-link>
        <template v-slot:prevButton>
            <svg width="31" height="22" class="banner-slider__arrows banner-slider__arrow-prev">
                <use href="./../assets/icons.svg#homePageSliderArrowLeft"></use>
            </svg>
        </template>
        <template v-slot:nextButton>
            <svg width="31" height="22" class="banner-slider__arrows banner-slider__arrow-next">
                <use href="./../assets/icons.svg#homePageSliderArrowRight"></use>
            </svg>
        </template>
    </VueAgile>
</template>
 
<script>
import { VueAgile } from 'vue-agile'
 
export default {
    name: 'home-page-slider',
    components: {
        VueAgile,
    },
    data() {
        return {
            bannerItem: [
                {
                    id: 0,
                    buttom: 'Анимация', 
                    title: 'Подготовка спрайтов для анимации в Unity',
                    text: 'Спрайты должны немного отличаться друг от друга, чтобы было заметно движение.',
                    src: require('./../assets/images/components/HomePageSlider/Image.png'),
                    srcRetina: require('./../assets/images/components/HomePageSlider/Image@2x.png'), 
                },                              
                {
                    id: 2,
                    buttom: 'slide 2',
                    title: 'Title slider2',
                    text: 'text slider 2',
                    src: require('./../assets/images/components/HomePageSlider/Image.png'),
                    srcRetina: require('./../assets/images/components/HomePageSlider/Image@2x.png'), 
                },                              
                {
                    id: 3,
                    buttom: 'slide 3',
                    title: 'Title slider3',
                    text: 'text slider 3',
                    src: require('./../assets/images/components/HomePageSlider/Image.png'),
                    srcRetina: require('./../assets/images/components/HomePageSlider/Image@2x.png'), 
                },                              
            ]
        }
    }   
}
</script> 

<style lang="scss">
    .banner-slider {
        &__wrapper {
            max-width: 1920px;
            width: 100%;

            & .agile__actions {
                max-width: 1200px;
                width: 100%;
                margin: 0 auto;
                padding-right: 15px;
                padding-left: 15px;
                box-sizing: border-box;
                position: absolute;
                bottom: 50px;
                left: 50%;
                transform: translate(-50%, 0);

                @media (max-width:991px) {
                    bottom: 10px;
                }
            }

            & .agile__dots {
                align-items: flex-end;
            }

            & .agile__dot {
                width: 70px;
                height: 2px;
                background-color: #fff;

                &:not(:last-child) {
                    margin-right: 30px;
                    @media (max-width:767px) {
                        margin-right: 10px;
                    }
                }

                @media (max-width:767px) {
                    width: 30px;
                }
            }

            & .agile__dot--current {
                background-color: #14A5DA;
            }
        }

        &__banner {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top;
            position: absolute;
            z-index: -1;
        }

        &__item {
            height: 600px;
            box-sizing: border-box;
            background-repeat: no-repeat;
            background-position: top;

            @media (max-width:991px) {
                height: 400px;
            }

            @media (max-width:767px) {
                height: 300px;
            }

            @media (max-width:480px) {
                height: 240px;
            }

            &-filter {
                width: 100%;
                height: 100%;
                padding: {
                    top: 116px;
                    bottom: 50px
                };
                box-sizing: border-box;
                background-color: rgba($color: #000, $alpha: 0.4);

                @media (max-width: 991px) {
                    padding: {
                        top: 100px;
                        bottom: 40px
                    };
                }

                @media (max-width: 767px) {
                    padding: {
                        top: 100px;
                    };
                }
                @media (max-width: 767px) {
                    padding: {
                        top: 75px;
                    };
                }
                @media (max-width: 480px) {
                    padding: {
                        top: 25px;
                    };
                }
            }
        }

        &__btn {
            padding: 6px 14px;
            margin-bottom: 30px;
            border-radius: 2px;
            font-size: 14px;
            font-weight: 500;
            text-transform: uppercase;
            color: #fff;
            background-color: #14A5DA;
            @media (max-width:767px) {
                margin-bottom: 15px;
            }
        }

        &__title {
            max-width: 765px;
            margin-bottom: 25px;
            display: block;
            font-size: 46px;
            font-weight: 600;
            text-transform: uppercase;
            color: #fff;

            @media (max-width:991px) {
                max-width: 500px;
                font-size: 30px;
            }

            @media (max-width:768px) {
                font-size: 16px;
                margin-bottom: 10px;
            }
        }

        &__text {
            max-width: 660px;
            font-size: 24px;
            line-height: 1.2;
            color: #fff;
            @media (max-width:991px) {
                max-width: 425px;
                font-size: 19px;
            }
            @media (max-width:768px) {
                font-size: 14px;
            }
        }

        &__arrows {
            fill: #fff;

            @media (max-width:767px) {
                width: 17px;
                height: 12px;
            }
        }
    }
</style>