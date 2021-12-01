<template>
  <div class="parallax-container">
    <div ref="parallax" class="parallax">
      <img src="../assets/frame-1_fit_medium.png" />
    </div>
    <div class="container">
      <div class="row upper-part">
        <div class="col m6">
          <h4>DIGOSSCHOOL - Онлайн школа</h4>
          <h3>Изчучения иностранных<br />языков.</h3>
        </div>
        <div class="col m6 addition">
          <h6>
            Громкостнoй прогрессийный период традиционен. Также контрапункт
            контрастных фактур, и это особенно заметно у Чарли Паркера или Джона
            Колтрейна,
          </h6>
        </div>
      </div>

      <div class="line"></div>

      <div class="row features">
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>500</p>
            <p class="description">Выпускников</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>20</p>
            <p class="description">Преподавателей</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>5</p>
            <p class="description">Программ обучения</p>
          </div>
        </div>
        <div class="col m3">
          <div class="feature-block">
            <p class="strong-text">>30</p>
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
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.container {
  font-family: @dop-font;
  letter-spacing: .8px;
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
.line {
  height: 2px;
  width: 100%;
  background-color: #f1968f;
  margin: 50px 0;
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
