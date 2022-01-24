<template>
  <div class="container">
    <div ref="carousel" class="carousel wow fadeInDown">
      <a v-for="quote of quotes" :key="quote.quote" class="carousel-item abc"
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
@import url("../assets/mainStyle.less");
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
@media only screen and (max-width: 600px) {
  .carousel .carousel-item {
    width: 100%;
    height: 300px;
  }
  .carousel {
    perspective: none;
  }
}
</style>
