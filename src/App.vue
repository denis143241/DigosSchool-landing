<template>
  <div @mousemove="getMousePos" class="header-page">
    <my-header />
    <div class="container">
      <div class="row header-main-info">
        <div class="col m8 wow fadeInLeft">
          <img src="./assets/Ellipse.png" />
          <transition
            :duration="1500"
            enter-active-class="animated fadeIn"
            leave-active-class="animated fadeOut"
          >
            <div :key="firstLineTitle" class="header-title">
              {{ firstLineTitle }}<br />{{ secondLineTitle }}
            </div>
          </transition>
          <div class="btns">
            <div class="row">
              <div class="col m4">
                <a href="#about"
                  ><my-btn class="addition-for-btn">Узнать больше</my-btn></a
                >
              </div>
              <div class="col m4">
                <a href="#test"
                  ><my-btn color="f1968f" class="addition-for-btn"
                    >К практике</my-btn
                  ></a
                >
                <!-- <my-btn color="FFCC80"> К практике </my-btn> -->
              </div>
            </div>
          </div>
        </div>
        <div class="col m4 flags">
          <div
            v-for="(circle, idx) in circles"
            :key="circle.id"
            class="circlesFlag-row wow fadeInRight"
            :data-wow-delay="`${idx * 100}ms`"
          >
            <transition name="my-flip">
              <div
                :key="firstLineTitle"
                class="circle-flag"
                :id="circle.id"
                :style="{
                  left: `${circle.sign1}${posX}%`,
                  top: `${circle.sign2}${posY}%`,
                  background: `url(${img}) no-repeat center center`,
                  backgroundSize: '100%',
                }"
              ></div>
            </transition>
          </div>
        </div>
      </div>
    </div>
  </div>

  <parallax-block />

  <famous-quots />

  <section id="targets">
    <main-title>Цели изучения иностранного языка</main-title>
    <div class="container">
      <div class="row">
        <div class="col m6">
          <async-target-block
            :col="1"
            :img="targetsData[0].img"
            :title="targetsData[0].title"
            :addition="targetsData[0].additions"
          />
          <async-target-block
            :col="1"
            :img="targetsData[1].img"
            :title="targetsData[1].title"
            :addition="targetsData[1].additions"
          />
          <async-target-block
            :col="1"
            class="last"
            :img="targetsData[2].img"
            :title="targetsData[2].title"
            :addition="targetsData[2].additions"
          />
        </div>
        <div class="col m6 shifted">
          <async-target-block
            :col="2"
            :img="targetsData[3].img"
            :title="targetsData[3].title"
            :addition="targetsData[3].additions"
          />
          <async-target-block
            :col="2"
            :img="targetsData[4].img"
            :title="targetsData[4].title"
            :addition="targetsData[4].additions"
          />
        </div>
      </div>
    </div>
  </section>

  <simple-test />

  <lessons-block />

  <answer-block />

  <reviews-block />

  <my-calendar />

  <my-footer />
</template>

<script>
// [х] 1. Добить на компоненты
// [] 2. Шапку на главном экране сделать бесцветной, когда экран уедет ниже главного покрасить ее и закрепить в вверху

import myBtn from "./components/myBtn.vue";
import myHeader from "./components/myHeader.vue";
import parallaxBlock from "./components/parallaxBlock.vue";
import famousQuots from "./components/famousQuots.vue";
import asyncTargetBlock from "./components/asyncTargetBlock.vue";
import mainTitle from "./components/mainTitle.vue";
import simpleTest from "./components/simpleTest.vue";
import lessonsBlock from "./components/lessonsBlock.vue";
import answerBlock from "./components/answerBlock.vue";
import reviewsBlock from "./components/reviewsBlock.vue";
import myCalendar from "./components/myCalendar.vue";
import myFooter from "./components/myFooter.vue";

// import WOW from "../node_modules/wowjs/dist/wow";
import { WOW } from "wowjs";

export default {
  components: {
    myBtn,
    myHeader,
    parallaxBlock,
    famousQuots,
    asyncTargetBlock,
    mainTitle,
    simpleTest,
    lessonsBlock,
    answerBlock,
    reviewsBlock,
    myCalendar,
    myFooter,
  },
  created() {
    let currentLanguage = this.foreignBox[0];
    this.firstLineTitle = currentLanguage.title1;
    this.secondLineTitle = currentLanguage.title2;
    this.img = currentLanguage.img;
  },
  mounted() {
    // const wow = new WOW().init();
    // console.log(wow);
    new WOW().init();
    setInterval(() => {
      let randEl = Math.floor(Math.random() * this.foreignBox.length);
      while (this.img == this.foreignBox[randEl].img) {
        randEl = Math.floor(Math.random() * this.foreignBox.length);
      }
      let currentLanguage = this.foreignBox[randEl];
      this.firstLineTitle = currentLanguage.title1;
      this.secondLineTitle = currentLanguage.title2;
      this.img = currentLanguage.img;
    }, 5000);
  },
  data() {
    return {
      color: "#555",
      mouseX: null,
      mouseY: null,
      firstLineTitle: "",
      secondLineTitle: "",
      img: "",
      seems: { name: 1 },
      circles: [
        { sign1: "", sign2: "", id: "first", sims: this.seems },
        { sign1: "", sign2: "-", id: "second", sims: this.seems },
        { sign1: "-", sign2: "", id: "third", sims: this.seems },
        { sign1: "-", sign2: "-", id: "forth", sims: this.seems },
        { sign1: "", sign2: "", id: "fiveth", sims: this.seems },
      ],
      foreignBox: [
        {
          title1: "Discover the",
          title2: "world with us!",
          img: require("./assets/united-kingdom.png"),
        },
        {
          title1: "¡Descubre el",
          title2: "mundo con nosotros!",
          img: require("./assets/spain.png"),
        },
        {
          title1: "Scopri il",
          title2: "mondo con noi!",
          img: require("./assets/italy.png"),
        },
        {
          title1: "Entdecke mit",
          title2: "uns die welt!",
          img: require("./assets/germany.png"),
        },
        {
          title1: "Découvrez le",
          title2: "monde avec nous!",
          img: require("./assets/france.png"),
        },
      ],
      targetsData: [
        {
          img: require("./assets/work.png"),
          title: "Для работы",
          additions: [
            "Общаться с иностранными партнерами",
            "Общаться в командировках",
            "Посещать международные конференции",
          ],
        },
        {
          img: require("./assets/travelling.png"),
          title: "Для путешествий",
          additions: ["С легкостью находить контакт с людьми в поездке"],
        },
        {
          img: require("./assets/me.png"),
          title: "Для себя",
          additions: [
            "Общение с друзьями инострацами",
            "Просмотр фильмов и чтение книг в оригинале",
            "Тренировка памяти",
          ],
        },
        {
          img: require("./assets/exam.png"),
          title: "Для ЕГЭ",
          additions: [
            "Подтянуть знания в рамках школьной/университетской программы, улучшить успеваемость",
          ],
        },
        {
          img: require("./assets/studying.png"),
          title: "Для обучения за рубежом",
          additions: [
            "Школа/университет/магистратура/аспирантура",
            "Будет подобрана индивидуальная программа по подготовке",
          ],
        },
      ],
    };
  },
  methods: {
    getMousePos(event) {
      this.mouseX = event.clientX;
      this.mouseY = event.clientY;
    },
  },
  computed: {
    posX() {
      return (this.mouseX / window.innerWidth) * 7;
    },
    posY() {
      return (this.mouseY / 792) * 7;
    },
  },
};
</script>

<style lang="less" scoped>
@import "~materialize-css/dist/css/materialize.min.css";
@import url("./assets/mainStyle.less");
.my-flip-enter-active {
  animation: my-flip-enter-anim 1s;
}
.my-flip-leave-active {
  animation: my-flip-leave-anim 1s;
}
@keyframes my-flip-enter-anim {
  0% {
    opacity: 0;
    transform: scale(1) rotateY(180deg);
  }
  49% {
    transform: scale(1.1);
    opacity: 0;
  }
  50% {
    opacity: 1;
    transform: scale(1.1) rotateY(-90deg);
  }
  100% {
    transform: scale(1) rotateY(0deg);
  }
}
@keyframes my-flip-leave-anim {
  0% {
    transform: scale(1) rotateY(0deg);
  }
  49% {
    transform: scale(1.1);
    opacity: 1;
  }
  50% {
    opacity: 0;
    transform: scale(1.1) rotateY(-90deg);
  }
  100% {
    opacity: 0;
    transform: scale(1) rotateY(180deg);
  }
}
.last {
  margin-bottom: 0 !important;
}
.shifted {
  margin-top: 150px;
}
.test-btn {
  position: relative;
  text-align: center;
  border: none !important;
  &:hover {
    animation: 1s border-around-animation;
  }
}
.span-left {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 1px;
  background-color: #000;
}
@keyframes border-around-animation {
  0% {
    .span-left {
      position: absolute;
      top: 0;
      left: 0;
      height: 0;
      width: 0;
      background-color: #000;
    }
  }
  100% {
    color: red;
    .span-left {
      position: absolute;
      top: 0;
      left: 0;
      height: 0%;
      width: 0;
      background-color: #000;
    }
  }
}
button {
  &:focus {
    background: none;
  }
}
body {
  overflow: hidden;
}
.circlesFlag-row {
  position: relative;
  width: 100%;
  height: 100px;
}
.header-page {
  height: 100vh;
  background: #f8f8f8;
}
.header-title {
  font-family: @main-font;
  top: 0;
  left: 0;
  position: absolute;
  font-size: 65px;
  font-weight: 900;
  margin: 50px 0 0 40px;
}
.header-main-info {
  position: relative;
  margin-top: 90px;
}
.btns {
  margin-top: 20px;
  position: relative;
}
.addition-for-btn {
  margin: 70px 0 0 40px;
  width: 100%;
}
// При появлении флага выводить его с animate bounceIn
.circle-flag {
  border-radius: 100%;
  background: #000;
  position: absolute;
  transition: 0.1s all; // Добавить delay мб и не надо.
  box-shadow: 8px 4px 7px rgba(0, 0, 0, 0.3);
}
#first {
  width: 120px;
  height: 120px;

  background: #f17f77 url("assets/germany.png") no-repeat center center;
  background-size: 100%;
}
#second {
  width: 80px;
  height: 80px;
  margin-left: 70%;
  background-color: #e0665d;
}
#third {
  width: 60px;
  height: 60px;
  margin-left: 40%;
  background-color: #c77069;
}
#forth {
  width: 50px;
  height: 50px;
  margin-left: 80%;
  background-color: #f59a9a;
}
#fiveth {
  width: 40px;
  height: 40px;
  margin-left: 20%;
  background-color: #e45a5a;
}
.common {
  background: none;
}
.my-red {
  background: #f1968f;
}
.fz-50 {
  font-size: 60px !important;
}
</style>

<style lang="less">
html {
  scroll-behavior: smooth;
}
</style>
