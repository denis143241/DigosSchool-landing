<template>
  <div class="test-app">
    <transition
      enter-active-class="animated fadeInRight"
      leave-active-class="animated fadeOutLeft"
    >
      <div v-if="step === 'before'" class="before-test">
        <div class="container">
          <main-title class="main-title"
            >Узнай свой уровень знаний прямо сейчас</main-title
          >
          <p>выбери один из предложенных языков и нажми начать</p>
          <div class="row btns">
            <div class="col m1"></div>
            <list-of-languages :size="2" @stateLang="stateLang" />
          </div>
          <div class="row">
            <div class="col m4 offset-m4 start-btn">
              <my-btn color="f1968f" class="start" @click="startTest"
                >Начать</my-btn
              >
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition
      enter-active-class="animated fadeInRight"
      leave-active-class="animated fadeOutLeft"
    >
      <div v-if="step === 'test'" class="test">
        <en-test v-if="lang === 'Английский'" @end="endTest" />
        <div v-else class="sorry">
          <p>Извините, данный тест пока не доступен :(</p>
          <div class="row">
            <div class="col m2 offset-m5">
              <my-btn @click="step = 'before'">Назад</my-btn>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition
      enter-active-class="animated fadeInRight"
      leave-active-class="animated fadeOutLeft"
    >
      <div v-if="step === 'results'" class="completed">
        <h4>Итого результат {{ score }} из 10</h4>
        <p>{{ aboutResult }}</p>
      </div>
    </transition>
  </div>
</template>

<script>
import mainTitle from "./mainTitle.vue";
import myBtn from "./myBtn.vue";
import enTest from "./enTest.vue";
import listOfLanguages from "./listOfLanguages.vue";
export default {
  components: {
    mainTitle,
    myBtn,
    enTest,
    listOfLanguages,
  },
  data() {
    return {
      score: 0,
      lang: "",
      step: "before",
    };
  },
  computed: {
    aboutResult() {
      return this.score > 5
        ? "Здорово! Присоединяйтесь к нам и повышайте свой уровень владения языком вместе с нами"
        : "Вы новичок? Ничего страшного, с нашими преподавателями вы поднимите свой уровень\n до pre-intermidiate всего за 1 меясяц ";
    },
  },
  methods: {
    endTest(data) {
      this.step = "results";
      this.score = data.score;
    },
    stateLang(data) {
      this.lang = data.lang;
      console.log(this.lang);
    },
    startTest() {
      this.step = "test";
    },
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
h4 {
  font-family: @dop-font;
  font-weight: 900;
  text-align: center;
  letter-spacing: .8px;
}
.main-title {
  margin-bottom: 20px !important;
}
.sorry p {
  font-size: 30px;
  text-align: center;
  font-weight: 500;
}
.test-app {
  margin: 170px 0 150px;
  position: relative;
  min-height: 417px;
}
.test {
  position: absolute;
  width: 100% !important;
  height: 100% !important;
  top: 0;
  left: 0;
}
p {
  font-family: @dop-font;
  letter-spacing: 0.9px;
  font-size: 16px;
  color: @dop-color;
  text-align: center;
  font-weight: 400;
}
.start-btn {
  display: flex;
  justify-content: center;
  align-items: center;
}
.start {
  width: 60%;
}
.btns {
  margin: 100px 0 50px;
}
h6 {
  width: 92%;
  margin-top: 60px;
  text-align: center;
  font-size: 13px;
  font-weight: 700;
  margin-bottom: 0;
}
.zero {
  color: rgba(204, 3, 3, 0);
}
</style>
