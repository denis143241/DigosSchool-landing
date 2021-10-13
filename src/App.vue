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
        <div class="col m6">
          <div class="header-title">Discover the<br />world with us!</div>
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
        <div class="col m6 flags">
          <div class="circlesFlag-row">
            <div
              class="circle-flag"
              id="first"
              :style="{ left: `${posX}%`, top: `${posY}%` }"
            ></div>
          </div>
          <div class="circlesFlag-row">
            <div
              class="circle-flag"
              id="second"
              :style="{ left: `${posX}%`, top: `${-posY}%` }"
            ></div>
          </div>
          <div class="circlesFlag-row">
            <div
              class="circle-flag"
              id="third"
              :style="{ left: `${-posX}%`, top: `${posY}%` }"
            ></div>
          </div>
          <div class="circlesFlag-row">
            <div
              class="circle-flag"
              id="forth"
              :style="{ left: `${-posX}%`, top: `${-posY}%` }"
            ></div>
          </div>
          <div class="circlesFlag-row">
            <div
              class="circle-flag"
              id="fiveth"
              :style="{ left: `${posX}%`, top: `${posY}%` }"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      color: "#555",
      mouseX: null,
      mouseY: null,
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
      return (this.mouseY / window.innerHeight) * 7;
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
  background: #f8f8f8 url("assets/main-bg.png") no-repeat center center;
}
.header-title {
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
  margin-top: 90px;
}
.btns {
  margin-top: 140px;
}
.circle-flag {
  border-radius: 100%;
  background: #000;
  position: absolute;
  transition: 0.1s all; // Добавить delay мб и не надо.
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}
#first {
  width: 100px;
  height: 100px;
  margin-left: 40%;
  background: #f17f77 url('assets/france.png') no-repeat center center;
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
  margin-left: 50%;
  background-color: #c77069;
}
#forth {
  width: 50px;
  height: 50px;
  margin-left: 80%;
  background-color: #f59a9a;
}
#fiveth {
  width: 30px;
  height: 30px;
  margin-left: 40%;
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
</style>
