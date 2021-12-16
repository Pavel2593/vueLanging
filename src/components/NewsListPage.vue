<template>
    <div class="news-list-page">
        <router-link to="/About"
        v-for="feed in news" :key="feed.id"
        class="news-list-page__wrapper"
        >
            <img
            class="news-list-page__img"
            :src="feed.src"
            :srcset="feed.srcRetina+' 2x'"
            alt="рисунок новости">
        </router-link>
    </div>
</template>

<script>
export default {
    name: 'NewsList',
    props: {
        news: {
            type: Array,
            required: true,
        }
    },
    data() {
        return {
            limit: 3,
        }
    },
}
</script>

<style lang="scss">
    .news-list-page {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        @media (max-width: 1199px) {
            align-items: center;
            flex-direction: column;
        }

        &__wrapper {
            margin-bottom: 30px;
            max-width: 570px;
            width: 100%;
            height: 300px;

            @media (max-width:479px) {
                margin-bottom: 20px;
                height: 200px;
            }

            &:nth-child(2) {
                @media (max-width: 1199px) {
                    order: -1;
                }
            }

            &:nth-child(3) {
                @media (min-width: 1200px) {
                    max-width: 100%;
                }
            }        
        }

        &__img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }
</style>