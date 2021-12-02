<template>
  <div class="full-block">
    <div class="parallax-container">
      <div ref="parallax" class="parallax">
        <!-- <img src="../assets/sky-short.jpg" /> -->
        <img src="../assets/frame-2new.png" alt="" />
      </div>
    </div>
    <div class="container absolute-container">
      <h4>Что говорят наши<br />выпускники?</h4>
      <div class="cards">
        <review-card
          v-for="(card, idx) in reviews"
          :key="card"
          class="my-card wow fadeInUp"
          :data-wow-delay="`${idx * 100 + 300}ms`"
          :person="card"
        ></review-card>
      </div>
    </div>
  </div>
</template>

<script>
import reviewCard from "./reviewCard.vue";
export default {
  components: {
    reviewCard,
  },
  data() {
    return {
      reviews: [
        {
          name: "Alekseev Ivan",
          work: "Менеджер",
          img: require("../assets/customer-2.jpg"),
          text: "Отличная школа! Очень удобный формат обучения! Сам выбираешь время, которое тебе удобно, сам выбираешь преподавателя по их резюме и записи голосового резюме на английском. Интересные упражнения и домашнее задание",
        },
        {
          name: "Mikhailova Nastya",
          work: "Дизайнер",
          img: require("../assets/customer-1.jpg"),
          text: "Сбалансированные онлайн-курсы, бесплатные блоки тренировок, разговорные клубы, блог, мобильное приложение. Долго искала годный ресурс для самостоятельного изучения английского, наткнулась полгода назад, до сих пор радуюсь.",
        },
        {
          name: "Sidorov Mickhail",
          work: "Фронтенд-разработчик",
          img: require("../assets/customer-3.jpg"),
          text: "Мой сын Глеб занимается в школе уже 4 год и результат обучения очень заметен. Мне нравится системный подход к обучению и аттестация, где определяется уровень знаний. Атмосфера обучения превосходная.",
        },
      ],
    };
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.full-block {
  position: relative;
  width: 100%;
  margin-bottom: 300px;
}
.parallax-container {
  height: 500px;
  margin: 0 auto;
  border-radius: 20px;
  width: 90%;
}
.absolute-container {
  position: absolute;
  top: 0;
  z-index: 2;
  left: 50%;
  transform: translateX(-50%);
}
.cards {
  display: flex;
  width: 100%;
  justify-content: space-around;
  margin: 100px auto 0 0;
}
h4 {
  font-family: @dop-font;
  letter-spacing: 1px;

  color: #fff;
  font-weight: 700;
  text-transform: uppercase;
  font-size: 50px;
  margin-top: 50px;
  // margin-left: 30px;
}
</style>
