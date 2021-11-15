<template>
  <v-app dark>
    <LpNavigation />
    <v-main>
      <section class="lp-page-container py-16 px-16">
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
