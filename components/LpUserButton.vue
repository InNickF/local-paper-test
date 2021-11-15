<template>
  <v-btn
    class="
      user-button
      black--text
      pr-1
      d-none d-lg-inline-flex d-xl-inline-flex
    "
    color="primary"
    rounded
    large
  >
    Nick fuenmayor
    <span class="user-icon pa-2 ml-2 rounded-xl elevation-4">
      <v-icon class="white--text"> mdi-account </v-icon>
    </span>
  </v-btn>
</template>
<style scoped>
.user-button {
  margin-right: -8px;
}
.user-icon {
  background: var(--lp-background);
}
</style>
