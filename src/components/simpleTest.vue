<template>
  <div class="test-app">
    <transition
      enter-active-class="animated fadeInRight"
      leave-active-class="animated fadeOutLeft"
    >
      <div v-if="step === 'before'" class="before-test">
        <div class="container">
          <main-title>Узнай свой уровень знаний прямо сейчас</main-title>
          <p>выбери один из предложенных языков и нажми начать</p>
          <div class="row btns">
            <div
              v-for="(lang, idx) in contries"
              :key="lang"
              :class="{ 'offset-m1': idx === 0 }"
              class="col m2"
            >
              <my-btn color="aeaeae" :bg="lang.flag"
                ><span class="zero">.</span></my-btn
              >
              <h6>{{ lang.text }}</h6>
            </div>
          </div>
          <div class="row">
            <div class="col m4 offset-m4 start-btn">
              <my-btn color="f1968f" class="start" @click="step = '1'"
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
        <!-- Тут надо сделать сам тест это будет отдельный компонент который будет эмитить конец (изменять переменную step) -->
      </div>
    </transition>
    <transition
      enter-active-class="animated fadeInRight"
      leave-active-class="animated fadeOutLeft"
    >
      <div v-if="step === 'completed'" class="completed">
        <!-- А тут нужен итог после теста который активируется после эмита блока выше -->
      </div>
    </transition>
  </div>
</template>

<script>
import mainTitle from "./mainTitle.vue";
import myBtn from "./myBtn.vue";
export default {
  components: {
    mainTitle,
    myBtn,
  },
  data() {
    return {
      step: "before",
      contries: [
        { text: "Английский", flag: require("../assets/britainForBtn.png") },
        { text: "Испанский", flag: require("../assets/spainForBtn.png") },
        { text: "Итальянский", flag: require("../assets/italyForBtn3.png") },
        { text: "Французский", flag: require("../assets/franceForBtn.png") },
        { text: "Немецкий", flag: require("../assets/germanyForBtn1.png") },
      ],
    };
  },
};
</script>

<style lang="less" scoped>
.test-app {
  margin: 150px 0;
}
p {
  text-align: center;
  font-weight: 900;
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
  margin: 100px 0 120px;
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
