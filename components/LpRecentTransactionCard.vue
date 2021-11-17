<template>
  <LpListCard>
    <template #icon>
      <span
        class="chip text-subtitle ma-0 lp-pulse"
        :class="`chip-${transaction.status.toLowerCase()}`"
      >
        {{ transaction.status }}
      </span>
    </template>
    <template #content>
      <section>
        <p class="text-subtitle mb-0">
          {{ transaction.date }} - {{ transaction.company }}
        </p>
        <h5 class="text-h5">{{ transaction.description }}</h5>
      </section>
    </template>
    <template #action>
      <div>
        <p class="text-subtitle mb-0 text-left text-sm-right">Value:</p>
        <p
          class="text-h5 font-weight-light mb-0"
          :class="{
            negative: transaction.quantity < 0,
            positive: transaction.quantity > 0,
          }"
        >
          {{ transaction.quantity > 0 ? '+' : '-' }}${{
            Math.abs(transaction.quantity)
              .toString()
              .replace(/\B(?=(\d{3})+(?!\d))/g, ',')
          }}
        </p>
      </div>
    </template>
  </LpListCard>
</template>
<script>
export default {
  name: 'LpRecentTransactionCard',
  props: {
    transaction: {
      type: Object,
      requiere: true,
      default: () => ({
        status: 'Processed',
        date: 'Nov 16, 2021',
        company: 'WPT LLC',
        description: 'Investment in Golden Beach',
        quantity: '100800',
      }),
    },
  },
}
</script>
<style scoped>
.chip {
  padding: 6px 6px 4px 6px;
  display: block;
  text-align: center;
  border-radius: 100px;
}
.chip-processed {
  background: rgba(105, 243, 180, 0.2);
  color: #00ffa9;
  border: solid 2px #00ffaa4b;
}
.chip-pending {
  background: rgba(243, 170, 105, 0.2);
  color: #ffbb00;
  border: solid 2px #ffbb004f;
}
.chip-cancelled {
  background: rgba(180, 180, 180, 0.5);
  color: #ffffff;
  border: solid 2px #ffffff3f;
}
.negative {
  color: rgb(255, 70, 70);
}
.positive {
  color: #00ffa9;
}
</style>
