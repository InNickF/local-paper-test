<template>
  <div class="lp-tabs-container">
    <v-tabs grow show-arrows>
      <v-tab>My recent transactions</v-tab>
      <v-tab>My recent documents</v-tab>
      <v-tab>My recent notifications</v-tab>
      <v-tab-item>
        <v-card>
          <v-card-text>
            <LpRecentTransactionCard
              v-for="(transaction, i) in transactions"
              :key="i"
              :transaction="transaction"
              :style="{
                '--lp-animation-delay': `0.${1 + i}s`,
                '--lp-entrance-scale': 1,
              }"
              class="lp-entrance"
            />
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card>
          <v-card-text>
            <LpRecentDocOrNotification
              v-for="(doc, i) in documents"
              :key="i"
              :item="doc"
              is-doc
              :style="{
                '--lp-animation-delay': `0.${1 + i}s`,
                '--lp-entrance-scale': 1,
              }"
              class="lp-entrance"
            />
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat>
          <v-card-text>
            <LpRecentDocOrNotification
              v-for="(notification, i) in notifications"
              :key="i"
              :item="notification"
              :style="{
                '--lp-animation-delay': `0.${1 + i}s`,
                '--lp-entrance-scale': 1,
              }"
              class="lp-entrance"
            />
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
export default {
  data() {
    return {
      transactions: [
        {
          status: 'Processed',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Investment in Golden Beach',
          quantity: '100800',
        },
        {
          status: 'Pending',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Payment of interest for 1010 Brickell',
          quantity: '1000',
        },
        {
          status: 'Cancelled',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Payment of interest for 1010 Brickell',
          quantity: '800',
        },
        {
          status: 'Processed',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Investment in Golden Beach',
          quantity: '-500000',
        },
        {
          status: 'Processed',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Payment of interest for 1010 Brickell',
          quantity: '305800',
        },
        {
          status: 'Processed',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Investment in Golden Beach',
          quantity: '400800',
        },
        {
          status: 'Pending',
          date: 'Nov 16, 2021',
          company: 'WPT LLC',
          description: 'Payment of interest for 1010 Brickell',
          quantity: '-100800',
        },
      ],
      documents: [
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
        {
          company: 'WPT LLC',
          date: 'Nov 16, 2021',
          name: 'Promissory Note for Golden Beach',
        },
      ],
      notifications: [
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
        {
          date: 'Nov 16, 2021',
          name: 'Golden Beach was successfully SOLD',
        },
      ],
    }
  },
}
</script>

<style>
.lp-tabs-container {
  border-radius: 22px;
  overflow: hidden;
}
.v-window__container {
  overflow-y: scroll;
  max-height: 345px;
}
.v-window__container::-webkit-scrollbar {
  width: 10px;
}
.v-window__container::-webkit-scrollbar-track {
  background: transparent;
}
.v-window__container::-webkit-scrollbar-thumb {
  background: rgba(194, 194, 194, 0.35);
}
.v-window__container::-webkit-scrollbar-thumb:hover {
  background: rgba(194, 194, 194, 0.7);
}
.theme--dark.v-tabs-items {
  background: #333d4836 !important;
}
.theme--dark.v-tabs > .v-tabs-bar {
  background: var(--lp-background);
}
.v-tab {
  word-break: break-all !important;
}
</style>
