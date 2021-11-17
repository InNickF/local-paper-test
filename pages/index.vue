<template>
  <v-row>
    <v-col cols="12" class="d-flex flex-wrap justify-space-between">
      <div>
        <h1 class="display-2 font-weight-bold">Dashboard</h1>
        <p>Here you can see a resume of all your information.</p>
      </div>
      <v-btn
        class="lp-entrance"
        rounded
        dark
        outlined
        color="primary"
        x-large
        @click.stop="filterDrawer = !filterDrawer"
      >
        Filter by
        <v-icon right>mdi-filter</v-icon>
      </v-btn>
    </v-col>
    <v-col cols="12">
      <section class="dashborad-grid">
        <h2 class="title-deals font-weight-light text--disabled lp-entrance">
          Active deals
        </h2>
        <LpAverageCard class="i-outs lp-entrance" :average="averages[0]">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="average-icon icon-animation"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M17 9V7a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2m2 4h10a2 2 0 002-2v-6a2 2 0 00-2-2H9a2 2 0 00-2 2v6a2 2 0 002 2zm7-5a2 2 0 11-4 0 2 2 0 014 0z"
            />
          </svg>
        </LpAverageCard>
        <LpAverageCard class="p-invest lp-entrance" :average="averages[1]">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="average-icon icon-animation"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"
            />
          </svg>
        </LpAverageCard>
        <h2 class="title-per font-weight-light text--disabled lp-entrance">
          Historical performance
        </h2>
        <LpAverageCard class="ti-date lp-entrance" :average="averages[2]">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="average-icon icon-animation"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"
            />
          </svg>
        </LpAverageCard>
        <LpAverageCard class="ti-distr lp-entrance" :average="averages[3]">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="average-icon icon-animation"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"
            />
          </svg>
        </LpAverageCard>
        <LpAverageCard class="tc-distr lp-entrance" :average="averages[4]">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="average-icon icon-animation"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="1.5"
              d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"
            />
          </svg>
        </LpAverageCard>
        <LpDoughnutChart class="doughnut lp-entrance" />
        <LpDashboardTabs class="navs lp-entrance" />
      </section>
    </v-col>
    <v-navigation-drawer
      v-model="filterDrawer"
      class="glass-effect"
      fixed
      floating
      app
      right
      temporary
      disable-resize-watcher
      width="400px"
    >
      <v-card
        height="100vh"
        flat
        class="pa-8 d-flex flex-wrap flex-column justify-space-between"
      >
        <div>
          <h2 class="text-h5 mb-4">Filter by:</h2>
          <v-text-field
            label="Name"
            hide-details="auto"
            class="mb-2"
          ></v-text-field>
          <v-autocomplete
            v-model="selected"
            :items="items"
            chips
            label="Company"
            full-width
            hide-details
            hide-no-data
            hide-selected
            multiple
            class="mb-4"
            single-line
          ></v-autocomplete>
          <v-menu
            v-model="fromMenu"
            :close-on-content-click="false"
            :nudge-right="40"
            transition="scale-transition"
            class="mb-3"
            offset-y
            min-width="auto"
          >
            <template #activator="{ on, attrs }">
              <v-text-field
                v-model="fromDate"
                label="From"
                prepend-inner-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker
              v-model="fromDate"
              @input="fromMenu = false"
            ></v-date-picker>
          </v-menu>
          <v-menu
            v-model="toMenu"
            :close-on-content-click="false"
            :nudge-right="40"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template #activator="{ on, attrs }">
              <v-text-field
                v-model="toDate"
                label="To"
                prepend-inner-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker
              v-model="toDate"
              @input="toMenu = false"
            ></v-date-picker>
          </v-menu>
        </div>
        <div>
          <v-btn
            class="mb-2"
            x-large
            dark
            block
            rounded
            color="primary"
            @click.stop="filterDrawer = !filterDrawer"
            >Apply filters</v-btn
          >
          <v-btn
            x-large
            dark
            block
            rounded
            plain
            @click.stop="filterDrawer = !filterDrawer"
            >Cancel</v-btn
          >
        </div>
      </v-card>
    </v-navigation-drawer>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      filterDrawer: false,
      selected: [],
      // averagePositions: [
      //   'i-outs',
      //   'p-invest',
      //   'ti-date',
      //   'ti-distr',
      //   'tc-distr',
      // ], TODO
      items: ['Company 1', 'Company 2'],
      fromMenu: false,
      fromDate: '',
      toMenu: false,
      toDate: '',
      averages: [
        {
          id: 1,
          title: 'Investments Outstanding',
          subtitle: '',
          value: 500000,
          dealsQantity: 3,
        },
        {
          id: 2,
          title: 'Pending Investment',
          subtitle: '',
          value: 1000000,
          dealsQantity: 10,
        },
        {
          id: 3,
          title: 'Total Invested to Date',
          subtitle: '',
          value: 10000000,
        },
        {
          id: 4,
          title: 'Total Income Distribution',
          subtitle: '',
          value: 10000000,
        },
        {
          id: 5,
          title: 'Total Capital Distribution',
          subtitle: '',
          value: 10000000,
        },
      ],
    }
  },
}
</script>
<style scoped>
.dashborad-grid {
  display: grid;
  grid-template-rows: auto;
  justify-items: stretch;
  gap: 24px;
  grid-template-columns: 1fr;
  grid-template-areas: 'title-deals' 'i-outs' 'p-invest' 'doughnut' 'title-per' 'ti-date' 'ti-distr' 'tc-distr' 'navs';
}
.title-deals {
  grid-area: title-deals;
}
.title-per {
  grid-area: title-per;
}
.i-outs {
  grid-area: i-outs;
}
.p-invest {
  --lp-animation-delay: 0.1s;
  grid-area: p-invest;
}
.ti-date {
  --lp-animation-delay: 0.2s;
  grid-area: ti-date;
}
.ti-distr {
  --lp-animation-delay: 0.3s;
  grid-area: ti-distr;
}
.tc-distr {
  --lp-animation-delay: 0.4s;
  grid-area: tc-distr;
}
.doughnut {
  --lp-animation-delay: 0.1s;
  grid-area: doughnut;
}
.navs {
  --lp-animation-delay: 0.2s;
  grid-area: navs;
}

.average-icon {
  width: 60px;
  color: var(--lp-primary);
}

@media (min-width: 600px) {
  .dashborad-grid {
    grid-template-columns: repeat(2, 1fr);
    grid-template-areas:
      'title-deals title-deals'
      'i-outs doughnut'
      'p-invest doughnut'
      'title-per title-per'
      'ti-date ti-distr'
      'tc-distr tc-distr'
      'navs navs';
  }
}

@media (min-width: 1200px) {
  .dashborad-grid {
    grid-template-columns: repeat(3, 1fr);
    grid-template-areas:
      'title-deals title-deals title-deals'
      'i-outs doughnut doughnut'
      'p-invest doughnut doughnut'
      'title-per title-per title-per'
      'ti-date ti-distr tc-distr'
      'navs navs navs';
  }
}

@media (min-width: 1500px) {
  .dashborad-grid {
    grid-template-columns: repeat(5, 1fr);
    grid-template-areas:
      'title-deals title-deals title-per title-per title-per'
      'i-outs p-invest ti-date ti-distr tc-distr'
      'doughnut doughnut navs navs navs';
  }
}
</style>
