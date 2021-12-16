<template>
    <default-desktop-header class="show-desktop-header"></default-desktop-header>
    <default-mobile-header class="show-mobile-header"></default-mobile-header>
</template>

<script>
import defaultDesktopHeader from '@/components/defaultDesktopHeader.vue'
import defaultMobileHeader from '@/components/defaultMobileHeader.vue'
export default {
    name: 'default-header',
    components: {
        defaultDesktopHeader,
        defaultMobileHeader,
    },
}
</script>

<style lang="scss">
    .show-desktop-header {
        @media (max-width: 767px) {
            display: none;
        }
    }

    .show-mobile-header {
        @media (min-width: 768px) {
            display: none;
        }
    }

</style>