<template>
  <defaultHeader/>
  <HomePageSlider/>
  <AboutCompany/>
  <NewsList :news="news"/>
  <SubscribeForm/>
  <defaultFooter/>
</template>

<script>
import defaultHeader from '@/components/defaultHeader.vue'
import HomePageSlider from '@/components/HomePageSlider.vue'
import AboutCompany from '@/components/AboutCompany.vue'
import NewsList from '@/components/NewsList.vue'
import SubscribeForm from '@/components/SubscribeForm.vue'
import defaultFooter from '@/components/defaultFooter.vue'

export default {
  name: 'Home',
  components: {
    defaultHeader, 
    HomePageSlider,
    AboutCompany,
    NewsList,
    SubscribeForm,
    defaultFooter
  },
  data() {
    return {
      news: [
        {
          id: 0,
          src: require('./../assets/images/components/NewsList/Image1.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image1@2x.png'), 
        },
        {
          id: 1,
          src: require('./../assets/images/components/NewsList/Image2.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image2@2x.png')
        },
        {
          id: 2,
          src: require('./../assets/images/components/NewsList/Image3.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image3@2x.png')
        },
        {
          id: 3,
          src: require('./../assets/images/components/NewsList/Image1.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image1@2x.png'), 
        },
        {
          id: 4,
          src: require('./../assets/images/components/NewsList/Image2.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image2@2x.png')
        },
        {
          id: 5,
          src: require('./../assets/images/components/NewsList/Image3.png'),
          srcRetina: require('./../assets/images/components/NewsList/Image3@2x.png')
        }
      ],
    }
  }
}
</script>
