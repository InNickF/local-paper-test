<template>
  <article
    class="article-grid py-2 px-1 mb-3 lp-box-shadow"
    :class="{ fluid: fluid }"
  >
    <div class="g-icon px-2"><slot name="icon"></slot></div>
    <div class="g-content px-2"><slot name="content"></slot></div>
    <div class="g-action px-2"><slot name="action"></slot></div>
  </article>
</template>
<script>
export default {
  name: 'LpListCard',
  props: {
    fluid: {
      type: Boolean,
      require: true,
      default: false,
    },
  },
}
</script>
<style scoped>
.article-grid {
  position: relative;
  display: grid;
  grid-template-rows: auto;
  grid-template-columns: 100px 1fr;
  grid-template-areas:
    'icon content'
    '.    action';
  border-radius: 18px;
  transition: all 0.25s ease-in-out;
}

.article-grid:hover {
  transform: scale(1.01);
}

.g-icon {
  grid-area: icon;
  place-self: start stretch;
  margin-top: 22px;
}
.g-content {
  grid-area: content;
}
.g-action {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  grid-area: action;
  place-self: start;
  margin-right: 0;
}

@media (min-width: 600px) {
  .article-grid {
    grid-template-columns: 130px calc(100% - 330px) 200px;
    grid-template-areas: 'icon content action';
  }
  .article-grid.fluid {
    grid-template-columns: 1fr 8fr 1fr;
    grid-template-areas: 'icon content action';
  }
  .g-action {
    place-self: center end;
    justify-content: flex-end;
    margin-right: 20px;
  }
  .g-icon {
    place-self: center stretch;
    margin-top: 0;
  }
}
</style>
