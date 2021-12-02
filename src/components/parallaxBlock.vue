<template>
  <div id="about" class="parallax-container">
    <div ref="parallax" class="parallax">
      <img src="../assets/frame-1_fit_medium.png" />
    </div>
    <div class="container">
      <div class="row upper-part">
        <div class="col m6 wow fadeInLeft">
          <h4>DIGOSSCHOOL - Онлайн школа</h4>
          <h3>Изчучения иностранных<br />языков.</h3>
        </div>
        <div class="col m6 addition wow fadeInRight">
          <h6>
            Громкостнoй прогрессийный период традиционен. Также контрапункт
            контрастных фактур, и это особенно заметно у Чарли Паркера или Джона
            Колтрейна,
          </h6>
        </div>
      </div>

      <div class="row features">
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text" ref="features">>{{ finished }}</p>
            <p class="description">Выпускников</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>{{ teachers }}</p>
            <p class="description">Преподавателей</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>{{ programs }}</p>
            <p class="description">Программ обучения</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>{{ bonuses }}</p>
            <p class="description">Различных бонусов</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// [] 1. Разбить на компоненты
// [] 2. Решить с процентом затемнения, опробовать 40%!

import M from "../../node_modules/materialize-css";
export default {
  mounted() {
    M.AutoInit();
    document.addEventListener("scroll", () => {
      if (this.isVisible() && this.scrollIs === false) {
        this.scrollNumbers();
      }
    });
  },
  data() {
    return {
      finished: 0,
      teachers: 0,
      programs: 0,
      bonuses: 0,
      scrollIs: false,
    };
  },
  methods: {
    isVisible() {
      let coords = this.$refs.features.getBoundingClientRect();
      let windowHeight = document.documentElement.clientHeight;
      let topVisible = windowHeight - coords.top;
      return topVisible - 30 > 0;
    },
    scrollNumbers() {
      (this.scrollIs = true),
        setInterval(() => {
          let counter = 0;
          this.finished < 500 ? (this.finished += 10) : (counter += 1);
          this.teachers < 20 ? this.teachers++ : (counter += 1);
          this.programs < 5 ? this.programs++ : (counter += 1);
          this.bonuses < 30 ? this.bonuses++ : (counter += 1);
          if (counter >= 4) return;
        }, 30);
    },
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.container {
  font-family: @dop-font;
  letter-spacing: 0.8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
}
.parallax-container {
  margin-bottom: 170px;
  height: 900px;
  color: #fff;
}
.features {
  width: 100%;
}
.upper-part {
  position: relative;
}
.feature-block {
  color: #fff;
  font-size: 20px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.strong-text {
  margin: 30px 0;
  font-size: 65px;
  font-weight: 900;
}
.addition {
  font-weight: 300 !important;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.description {
  letter-spacing: 1px;
  padding: 0;
  margin: 0;
  font-weight: 300;
  font-size: 20px;
  text-transform: uppercase;
}
h6 {
  text-align: center;
  max-width: 80%;
  font-weight: 300;
  font-size: 16px;
}
h4 {
  font-size: 22px;
  font-weight: 300;
  text-align: center;
  margin: 0;
}
h3 {
  font-family: @main-font;
  font-size: 40px;
  font-weight: 700;
  text-align: center;
  margin: 0;
}
</style>
