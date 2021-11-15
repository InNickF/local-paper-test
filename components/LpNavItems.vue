<template>
  <div>
    <v-btn
      v-for="(link, i) in links"
      :key="i"
      class="ml-4 d-none d-lg-inline-flex d-xl-inline-flex"
      rounded
      plain
      elevation="0"
      >{{ link }}</v-btn
    >
  </div>
</template>
<script>
export default {
  name: 'LpNavItems',
  props: {
    links: {
      type: Array,
      require: true,
      default: () => [],
    },
  },
}
</script>
