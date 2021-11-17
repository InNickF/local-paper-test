<template>
  <article
    ref="container"
    class="article-grid lp-box-shadow"
    :style="mouseEffect"
    @mousemove="mouseMove"
    @mouseleave="resetTrasnform"
  >
    <section class="icon"><slot></slot></section>
    <section class="options">
      <v-menu bottom left rounded="xl">
        <template #activator="{ on, attrs }">
          <v-btn dark icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>
        <v-list rounded>
          <v-list-item v-for="(option, i) in options" :key="i" link>
            <v-list-item-title>{{ option }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </section>
    <section class="title">
      <h4 class="font-weight-light text--secondary">{{ average.title }}</h4>
    </section>
    <section class="value">
      <div>
        <p class="display-1 ma-0">
          <strong
            >${{
              average.value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
            }}</strong
          >
        </p>
      </div>
      <div v-if="average.dealsQantity" class="mb-1">
        <small class="font-weight-light">
          <strong class="font-weight-bold">
            {{ average.dealsQantity }}
          </strong>
          {{ average.dealsQantity > 1 ? 'Deals' : 'Deal' }}
        </small>
      </div>
    </section>
  </article>
</template>
<script>
export default {
  name: 'LpAverageCard',
  props: {
    average: {
      type: Object,
      require: true,
      default: () => ({
        title: 'Average',
        subtitle: '',
        value: 0,
        dealsQantity: 0,
      }),
    },
  },
  data() {
    return {
      options: ['More details', 'Change Currency'],
      offset: {
        x: '',
        y: '',
        friction: 1 / 24,
      },
    }
  },
  computed: {
    mouseEffect() {
      return {
        transform: `perspective(600px)
                  rotateY(${this.offset.x}deg)
                  rotateX(${this.offset.y}deg)
                  scale(var(--scale))!important`,
      }
    },
  },
  methods: {
    mouseMove(e) {
      if (window.innerWidth > 1280) {
        const followX =
          this.$refs.container.offsetWidth / 2 -
          (e.clientX - this.$refs.container.offsetLeft)
        const followY =
          this.$refs.container.offsetHeight / 2 -
          (e.clientY - this.$refs.container.offsetTop)
        let x = 0
        let y = 0
        x += (-followX - x) * this.offset.friction
        y += (followY - y) * this.offset.friction
        this.offset.x = x
        this.offset.y = y
      }
    },
    resetTrasnform() {
      this.offset.x = 0
      this.offset.y = 0
    },
  },
}
</script>
<style scoped>
.article-grid {
  --scale: 1;
  transition: transform ease-in-out 0.25s !important;
  display: grid;
  width: 100%;
  gap: 12px;
  grid-template-columns: 1fr 36px;
  grid-template-rows: auto;
  grid-template-areas:
    'icon options'
    'title title'
    'value value';
}
.article-grid:hover {
  transition: transform ease-in-out 0.05s;
}
@media (min-width: 1280px) {
  .article-grid:hover {
    --scale: 1.05;
  }
}

.icon {
  grid-area: icon;
}
.options {
  grid-area: options;
}
.title {
  grid-area: title;
}
.value {
  margin-top: -12px;
  grid-area: value;
}
</style>
