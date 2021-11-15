<template>
  <v-menu rounded="b-xl" offset-y>
    <template #activator="{ attrs, on }">
      <v-btn
        class="
          user-button
          black--text
          ml-4
          pr-1
          d-none d-lg-inline-flex d-xl-inline-flex
        "
        color="primary"
        rounded
        large
        v-bind="attrs"
        v-on="on"
      >
        Nick fuenmayor
        <span class="user-icon pa-2 ml-2 rounded-xl elevation-4">
          <v-icon class="white--text"> mdi-account </v-icon>
        </span>
      </v-btn>
    </template>
    <v-list rounded>
      <v-list-item link>
        <v-list-item-title>Profile</v-list-item-title>
      </v-list-item>
      <v-list-item link>
        <v-list-item-title>Configuration</v-list-item-title>
      </v-list-item>
      <v-list-item link>
        <v-list-item-title
          ><span class="logout">Logout</span></v-list-item-title
        >
      </v-list-item>
    </v-list>
  </v-menu>
</template>
<style scoped>
.user-button {
  margin-right: -8px;
  transition: 0.2s ease-in-out all;
}
.user-icon {
  background: var(--lp-background);
}
.user-button[aria-expanded='true'] {
  border-radius: 22px 22px 0 0 !important;
}
</style>
