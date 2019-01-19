<template>
  <v-app>
    <!-- Header -->
    <vue-header></vue-header>
    <!-- Content -->
    <vue-content></vue-content>
    <!-- Footer -->
    <vue-footer></vue-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import VueHeader from './components/Header'
import VueContent from './components/Content'
import VueFooter from './components/Footer'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    VueHeader,
    VueContent,
    VueFooter
  },
  data () {
    return {
      //
    }
  }
}
</script>
