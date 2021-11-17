<template>
  <LpListCard fluid>
    <template #icon>
      <section class="d-flex justify-center align-content-center">
        <div class="icon-container pa-4 lp-pulse">
          <v-icon color="primary">
            {{ isDoc ? 'mdi-file-document' : 'mdi-bell' }}
          </v-icon>
        </div>
      </section>
    </template>
    <template #content>
      <section>
        <p class="text-subtitle mb-0">
          {{ item.date }} {{ item.company ? `- ${item.company}` : '' }}
        </p>
        <h5 class="text-h5">{{ item.name }}</h5>
      </section>
    </template>
    <template #action>
      <v-btn color="primary" rounded plain elevation="0"> View </v-btn>
    </template>
  </LpListCard>
</template>
<script>
export default {
  name: 'LpRecentDocOrNotification',
  props: {
    item: {
      type: Object,
      requiere: true,
      default: () => ({
        date: 'Nov 16, 2021',
        name: 'Investment in Golden Beach',
      }),
    },
    isDoc: {
      type: Boolean,
      require: true,
      default: false,
    },
  },
}
</script>
<style scoped>
.icon-container {
  background: #19cede21;
  height: 50px;
  width: 50px;
  display: flex;
  align-content: center;
  justify-content: center;
  border-radius: 50%;
  place-self: center center;
}
</style>
