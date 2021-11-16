<template>
  <v-app dark>
    <LpNavigation />
    <v-main>
      <section class="lp-page-container py-8 px-4 py-md-16 px-md-16">
        <Nuxt />
      </section>
      <LpFooter />
    </v-main>
  </v-app>
</template>

<script>
import LpNavigation from '~/components/LpNavigation.vue'
export default {
  data() {
    return {
      name: 'DefaultLayout',
      components: { LpNavigation },
    }
  },
}
</script>
<style>
.lp-page-container {
  min-height: calc(100vh - 70px);
}
</style>
