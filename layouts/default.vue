<template>
  <v-app dark>

    <!-- Navbar -->
    <navbar />
    <!-- End Navbar -->

    <!-- Content -->
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <!-- End Content -->

    <v-footer
      app
    >
      <span>&copy; StatusCake 2019. All rights reserved.</span>
    </v-footer>
  </v-app>
</template>

<script>

  import navbar from './navbar'

  export default {
    components: {
      navbar
    },
    data() {
      return {
        title: 'StatusCake'
      }
    }
  }
</script>
