<template>
  <div @mousemove="getMousePos" class="header-page">
    <nav>
      <div class="container">
        <div class="nav-wrapper">
          <a href="#" class="brand-logo">DIGOS<strong>SCHOOL</strong></a>
          <ul id="nav-mobile" class="right hide-on-med-and-down">
            <li><a class="nav-li" href="sass.html">О нас</a></li>
            <li><a class="nav-li" href="badges.html">Учебник</a></li>
            <li><a class="nav-li" href="collapsible.html">Тесты</a></li>
            <li><a class="nav-li" href="collapsible.html">Тесты</a></li>
            <li>
              <a class="nav-li" href="collapsible.html">8 900 400-55-44</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="container">
      <div class="row header-main-info">
        <div class="col m8">
          <img src="./assets/Ellipse.png">
          <div
            class="header-title"
            :class="{
              'fz-50':
                firstLineTitle === foreignBox[1].title1 ||
                firstLineTitle === foreignBox[2].title1 ||
                firstLineTitle === foreignBox[4].title1,
            }"
          >
            {{ firstLineTitle }}<br />{{ secondLineTitle }}
          </div>
          <div class="btns">
            <div class="row">
              <div class="col m4">
                <button class="my-btn common">Узнать больше</button>
              </div>
              <div class="col m4">
                <button class="my-btn my-red">К практике</button>
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
            <div
              class="circle-flag"
              :id="circle.id"
              :style="{
                left: `${circle.sign1}${posX}%`,
                top: `${circle.sign2}${posY}%`,
                background: `url(${img}) no-repeat center center`,
                backgroundSize: '100%',
              }"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const randEl = Math.floor(Math.random() * 5);
    let currentLanguage = this.foreignBox[randEl];
    this.firstLineTitle = currentLanguage.title1;
    this.secondLineTitle = currentLanguage.title2;
    this.img = currentLanguage.img;
  },
  data() {
    return {
      color: "#555",
      mouseX: null,
      mouseY: null,
      firstLineTitle: "",
      secondLineTitle: "",
      img: "",
      circles: [
        { sign1: "", sign2: "", id: "first" },
        { sign1: "", sign2: "-", id: "second" },
        { sign1: "-", sign2: "", id: "third" },
        { sign1: "-", sign2: "-", id: "forth" },
        { sign1: "", sign2: "", id: "fiveth" },
      ],
      foreignBox: [
        {
          title1: "Doscover the",
          title2: "world with us!",
          img: "/img/united-kingdom.6c562e43.png",
        },
        {
          title1: "¡Descubre el",
          title2: "mundo con nosotros!",
          img: "/img/spain.db9f43d8.png",
        },
        {
          title1: "Scopri il",
          title2: "mondo con noi!",
          img: "/img/italy.ec34fab4.png",
        },
        {
          title1: "Entdecke mit",
          title2: "uns die welt!",
          img: "/img/germany.5deb47d3.png",
        },
        {
          title1: "Découvrez le",
          title2: "monde avec nous!",
          img: "/img/france.3ac5c01c.png",
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
      // Исправить потенциальную ошибку связанную с высотой экрана InnerHeight
      // будет возвращать высоту всего экрана, а нам нужна высотка конкретного блока
      return (this.mouseY / 792) * 7;
    },
  },
};
</script>

<style lang="less" scoped>
@import "~materialize-css/dist/css/materialize.min.css";
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
nav {
  background: rgba(255, 255, 255, 0) !important;
  color: #000;
  box-shadow: none;
}
.nav-li {
  color: #000;
  &:hover {
    background: none;
  }
}
.brand-logo {
  color: #000;
  font-size: 25px;
  font-weight: 400;
  strong {
    font-weight: 700;
  }
}
.header-main-info {
  position: relative;
  margin-top: 90px;
}
.btns {
  margin-top: 20px;
}
// При появлении флага выводить его с animate bounceIn
.circle-flag {
  border-radius: 100%;
  background: #000;
  position: absolute;
  transition: 0.1s all; // Добавить delay мб и не надо.
  box-shadow: 4px 4px 7px rgba(0, 0, 0, 0.25);
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
.my-btn {
  font-weight: 600;
  margin: 70px 0 0 40px;
  border: 1px solid rgba(0, 0, 0, 1);
  width: 100%;
  padding: 12px 20px;
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
