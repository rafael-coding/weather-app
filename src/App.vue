<template>
  <main>
    <TimeBackground/>
    <img alt="Vue logo" src="./assets/logo.png">
    <section>
      <BoxContent/>
    </section>
  </main>
  <FooterComponent/>
</template>

<script>
//import components
import TimeBackground from './components/TimeBackground.vue'
import BoxContent from './components/BoxContent.vue'
import FooterComponent from './components/FooterComponent.vue'

export default {
  name: 'App',
  components: {
    TimeBackground,
    BoxContent,
    FooterComponent
  },
  data(){
    return {
      // api weather
      api_key: '8ee5579196e0ebc8f2a28c5e7ea6a397',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {},
    }
  },

  mounted(){

  }

}
</script>

<style>
 @import '../src/assets/app.css';

</style>
