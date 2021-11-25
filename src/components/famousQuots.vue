<template>
  <div class="famous-quots">
    <main-title class="title"
      >Цитаты известных людей о знании<br />иностранных языков</main-title
    >
    <my-carousel :quotes="quotes"></my-carousel>
  </div>
</template>

<script>
import mainTitle from "./mainTitle.vue";
import myCarousel from "./myCarousel.vue";
export default {
  components: {
    mainTitle,
    myCarousel,
  },
  data() {
    return {
      quotes: [
        {
          name: "Федерико Феллини",
          quote: "Другой язык – это другое видение жизни.",
        },
        {
          name: "Карл Великий",
          quote: "Владеть другим языком – значит иметь вторую душу.",
        },
        {
          name: "Вольфганг Гёте",
          quote:
            "Кто не знает иностранных языков, ничего не знает и о своём собственном.",
        },
        {
          name: "Эзра Паунд",
          quote:
            "Вся сумма человеческой мудрости не содержится только в одном каком-либо языке.",
        },
        {
          name: "Нельсон Мандела",
          quote:
            "Если вы поговорите с человеком на языке, который он понимает, вы обращаетесь к его голове. Если вы говорите с ним на его родном языке, вы обращаетесь к его сердцу.",
        },
      ],
    };
  },
};
</script>

<style lang="less" scoped>
.famous-quots {
  margin-bottom: 170px;
}
.title {
  margin-bottom: 0;
}
</style>
