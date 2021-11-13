<template>
  <div @mousemove="getMousePos" class="header-page">
    <my-header />
    <div class="container">
      <div class="row header-main-info">
        <div class="col m8">
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
                <my-btn>Узнать больше</my-btn>
              </div>
              <div class="col m4">
                <my-btn color="f1968f"> К практике </my-btn>
                <!-- <my-btn color="FFCC80"> К практике </my-btn> -->
              </div>
            </div>
          </div>
        </div>
        <div class="col m4 flags">
          <div
            v-for="circle in circles"
            :key="circle.id"
            class="circlesFlag-row"
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
</template>

<script>
// [] 1. Добить на компоненты
// [] 2. Шапку на главном экране сделать бесцветной, когда экран уедет ниже главного покрасить ее и закрепить в вверху

import myBtn from "./components/myBtn.vue";
import myHeader from "./components/myHeader.vue";
import parallaxBlock from "./components/parallaxBlock.vue";
import famousQuots from "./components/famousQuots.vue";
export default {
  components: { myBtn, myHeader, parallaxBlock, famousQuots },
  created() {
    let currentLanguage = this.foreignBox[0];
    this.firstLineTitle = currentLanguage.title1;
    this.secondLineTitle = currentLanguage.title2;
    this.img = currentLanguage.img;
  },
  mounted() {
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
  font-family: "Open Sans", sans-serif;
  height: 100vh;
  background: #f8f8f8;
}
.header-title {
  top: 0;
  left: 0;
  position: absolute;
  font-family: "Open Sans", sans-serif;
  font-size: 65px;
  font-weight: 700;
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
// .my-btn {
//   font-weight: 600;
//   margin: 70px 0 0 40px;
//   border: 1px solid rgba(0, 0, 0, 1);
//   width: 100%;
//   padding: 12px 20px;
// }
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
