<template>
    <section class="about-company page-wrapper">
        <router-link to="/about"><h2 class="about-company__title">{{title}}</h2></router-link>
        <div>
            <p class="about-company__text">{{text}}</p>
            <router-link to="/about" class="link">
                <p class="link__text" href="#">Подробнее</p>
                <svg width="18" height="13">
                  <use href="./../assets/icons.svg#blackRightArrow"></use>
                </svg>
            </router-link>
        </div>
    </section>
</template>

<script>
export default {
    name: 'AboutCompany',
    data() {
        return {
            title: 'О компании',
            text: 'Что-то более продвинутое делается с помощью покадровой анимации — когда для разных состояний объекта (стоит, идет, в прыжке, атакует) создается несколько спрайтов (двумерное изображение), которые сменяют друг друга с определенным интервалом.',
        }
    }
}
</script>

<style lang="scss">
  .about-company {
    padding: {
      top: 20px;
      bottom: 30px; 
    }

    @media (min-width:768px) {
      padding: {
        top: 70px;
        bottom: 80px
      };
      display: flex;
      justify-content: space-between;
    }

    &__title {
      margin-bottom: 10px;
      font-weight: bold;
      color: #000;
      white-space: nowrap;
      text-transform: uppercase;

      @media (min-width:768px) {
        margin-right: 30px;
        flex-shrink: 0;
      }

      @media (max-width: 767px) {
        text-align: center;
      }
    }

    &__text {
      max-width: 770px;
      margin-bottom: 20px;
      text-align: left;

      @media (min-width:768px) {
        margin-bottom: 50px;
      }
    }

    .link {
      display: flex;
      justify-content: center;
      align-items: center;
      @media (min-width:768px) {
        justify-content: flex-start;
      }

      &__text {
        margin-right: 5px;
        font-size: 10px;
        font-weight: 600;
        text-transform: uppercase;
        color: #000;

        @media (min-width:768px) {
          margin-right: 15px;
          font-size: 14px;
        }
      }

    }
  }
</style>