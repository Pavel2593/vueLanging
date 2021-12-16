<template>
    <section class="news-list page-wrapper">
        <div class="news-list__header">
            <router-link to="/About"><h2 class="news-list__title">Новости</h2></router-link>
            <router-link to="/About" class="news-list__link">Все новости</router-link>
        </div>
        <transition-group name="page-animation">
            <NewsListPage v-for="(pageItems, i) in pagesItemLists" :key="i" :news="pageItems"/>
        </transition-group>
        <button
            class="news-list__next-page"
            v-if="showButton()"
            @click="getPageList();">
            Показать еще
        </button>
    </section>
</template>

<script>
import NewsListPage from '@/components/NewsListPage.vue'
export default {
    name: 'NewsList',
    components: {
        NewsListPage,
    },
    props: {
        news: {
            type: Array,
            required: true,
        }
    },
    data() {
        return {
            pageColItems: 3,
            limitPages: 1,
            pagesItemLists: [
                this.news.slice(0, 3),
            ],
        }
    },
    methods: {
        getPageList() {          
            const nextPageItemsList = this.news.slice(
                this.pageColItems*this.limitPages,
                this.pageColItems*(this.limitPages+1)
            )
            this.limitPages += 1;
            this.pagesItemLists.push(nextPageItemsList);
        },
        showButton() {
            let result = true;
            if (this.news.length <= this.limitPages*this.pageColItems) {
                result = false;
            } else {
                result = true;
            }
            return result;
        }
    }
}
</script>

<style lang="scss">
    @import './../styles/_main/_colors';
    .news-list {
        padding-bottom: 80px;

        @media (max-width:767px) {
            padding-bottom: 30px;
        }

        &__header {
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
            @media (max-width:767px) {
                justify-content: center;
            }
        }

        &__title {
            font-weight: bold;
            color: #000;
            text-transform: uppercase;
        }

        &__link {
            font-size: 16px;
            color: $black;
            @media (max-width:767px) {
                display: none;
            }
        }

        &__next-page {
            margin: 20px auto 0;
            font-size: 14px;
            font-weight: 600;
            text-transform: uppercase;

            @media (max-width:767px) {
                margin: 0 auto;
                font-size: 10px;
            }
        }
    }
    .page-animation-item {
        display: inline-block;
        margin-right: 100px;
    }
    .page-animation-enter-active,
    .page-animation-leave-active {
        transition: all 1s ease;
    }
    .page-animation-enter-from,
    .page-animation-leave-to {
        opacity: 0;
        transform: translateY(300px);
    }
</style>