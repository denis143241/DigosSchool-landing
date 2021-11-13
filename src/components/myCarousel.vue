<template>
  <div class="container">
    <div ref="carousel" class="carousel">
      <a v-for="quote of quotes" :key="quote.quote" class="carousel-item"
        ><quote-card :quote="quote"></quote-card
      ></a>
    </div>
  </div>
</template>

<script>
import M from "../../node_modules/materialize-css";
import quoteCard from "./qouteCard.vue";
export default {
  props: {
    quotes: {
      type: Array,
    },
  },
  components: {
    quoteCard,
  },
  mounted() {
    document.addEventListener("DOMContentLoaded", () => {
      var elems = this.$refs.carousel;
      M.Carousel.init(elems, { numVisible: 3 });
    });
  },
};
</script>

<style lang="less" scoped>
.quote {
  width: 100%;
  height: 300px;
  background-color: #aeaeae;
}
.carousel .carousel-item {
  width: 500px;
}
.carousel {
  width: 100%;
  margin: 0 auto;
}
a:hover {
  cursor: context-menu;
}
</style>
