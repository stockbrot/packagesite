<template>
  <v-app dark id="app">
    <Navigation/>
    <component :is="aComponent"></component>
    <Footer/>
  </v-app>
</template>

<script>
import Blog from './components/Blog'
import About from './components/About'
import Home from './components/Home'
import Footer from './components/Footer'
import Navigation from './components/Navigation'
import EventBus from './eventbus.js'

export default {
  name: 'App',
  components: {
    Blog,
    Navigation,
    About,
    Home,
    Footer
  },
  data () {
    return {
      aComponent: 'Home'
    }
  },
  methods: {
    updateData: function (data) {
      this.aComponent = data.page
    }
  },
  mounted () {
    EventBus.$on('TOOLBAR_CLICKED', (payload) => {
      this.updateData(payload)
      console.log('Receiving Data: %s', payload)
    })
  }
}

</script>

<style>
</style>
