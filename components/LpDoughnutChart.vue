<template>
  <article class="article-grid lp-box-shadow">
    <span ref="containerD" class="ref"> </span>
    <h4 class="title text-center g-title font-weight-light text--secondary">
      Investments outstanding
    </h4>
    <div class="g-doughnut">
      <DoughnutChart
        style="width: 175px !important; height: 175px !important"
        class="mx-auto lp-pulse"
        :chart-data="doughnut.data"
        :options="doughnut.options"
      />
    </div>
    <div
      class="g-info text-center d-flex flex-column justify-center align-center"
    >
      <p
        v-for="(label, i) in doughnut.data.labels"
        :key="i"
        class="dot mb-0 text-subtitle-2 font-weight-light"
        :class="{
          'current-dot': i === 0,
          'late-dot': i === 1,
          'default-dot': i === 2,
        }"
      >
        {{ label }} (${{ doughnut.data.datasets[0].data[i] }} -
        {{
          (
            (doughnut.data.datasets[0].data[i] * 100) /
            doughnut.data.datasets[0].data.reduce(
              (previousValue, currentValue) => previousValue + currentValue
            )
          ).toFixed(2)
        }}%)
      </p>
    </div>

    <!-- <BarChart
      :chart-data="bar.data"
      style="height: 175px !important"
      :options="bar.options"
    /> -->
  </article>
</template>
<script>
export default {
  data() {
    return {
      doughnut: {
        data: {
          labels: ['Current', 'Late', 'Default'],
          datasets: [
            {
              label: 'Investments outstanding',
              data: [40000, 25000, 22000],
              backgroundColor: [
                'rgb(105, 243, 180)',
                'rgb(41, 214, 214)',
                'rgb(8, 104, 104)',
              ],
              hoverOffset: 0,
            },
          ],
        },
        options: {
          legend: {
            display: false,
          },
          elements: { arc: { borderColor: '#333d48' } },
        },
      },
      // bar: {
      //   data: {
      //     labels: ['Current', 'Late', 'Default'],
      //     datasets: [
      //       {
      //         data: [40000, 25000, 22000],
      //         backgroundColor: [
      //           'rgba(105, 243, 180, 0.7)',
      //           'rgba(41, 214, 214, 0.7)',
      //           'rgba(8, 104, 104, 0.7)',
      //         ],
      //         borderColor: [
      //           'rgb(105, 243, 180)',
      //           'rgb(41, 214, 214)',
      //           'rgb(8, 104, 104)',
      //         ],
      //         borderWidth: 1,
      //         borderRadius: 300,
      //       },
      //     ],
      //   },
      //   options: {
      //     maintainAspectRatio: false,
      //     legend: {
      //       display: false,
      //     },
      //     scales: {
      //       yAxes: [
      //         {
      //           ticks: {
      //             beginAtZero: true,
      //             fontColor: 'rgba(255,255,225,1)',
      //           },
      //           gridLines: {
      //             color: 'rgba(255,255,225,0.3)',
      //           },
      //         },
      //       ],
      //       xAxes: [
      //         {
      //           ticks: {
      //             fontColor: 'rgba(255,255,225,1)',
      //           },
      //           gridLines: {
      //             display: false,
      //           },
      //         },
      //       ],
      //     },
      //   },
      // },
    }
  },
}
</script>
<style scoped>
.article-grid {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto;
  gap: 12px;
  padding: 28px;
  grid-template-areas: 'title' 'doughnut' 'info';
}
.ref {
  position: absolute;
  top: 50%;
  left: 50%;
}
.g-title {
  grid-area: title;
}
.g-doughnut {
  grid-area: doughnut;
}
.g-info {
  grid-area: info;
}
.dot {
  margin-left: 20px;
}
.dot::before {
  content: '';
  position: relative;
  display: block;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  top: 16px;
  left: -20px;
}
.current-dot::before {
  background-color: rgb(105, 243, 180);
}
.late-dot::before {
  background-color: rgb(41, 214, 214);
}
.default-dot::before {
  background-color: rgb(8, 104, 104);
}
</style>
