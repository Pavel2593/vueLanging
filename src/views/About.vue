<template>
    <div class="block">
        <div>
            Это страница вместо всех кроме главной.)
        </div>
        <router-link to="/" class="block__link">Вернуться на главную</router-link>  
    </div>

</template>
<style lang="scss">
    .block {
        padding: 50px 0;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-size: 20px;
        font-weight: 600px;
        font-family: 'Montserrat';

        &__link {
            margin: 25px;
            color: #000;
            font-weight: 800;
        }
    }
</style>