<template>
  <nav class="wow fadeIn">
    <div class="container">
      <div class="nav-wrapper">
        <a href="#" class="brand-logo">DIGOS<strong>SCHOOL</strong></a>
        <ul id="nav-mobile" class="right hide-on-med-and-down">
          <li><a class="nav-li" href="#about">О нас</a></li>
          <li><a class="nav-li" href="#lessons">Учебник</a></li>
          <li><a class="nav-li" href="#test">Тесты</a></li>
          <li>
            <a
              class="nav-li"
              href="https://denis143241.github.io/ForeignSchool/"
              >Регистрация</a
            >
          </li>
          <li>
            <a class="nav-li" href="#">8 900 400-55-44</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
nav {
  font-family: @main-font;
  background-color: #f1968f !important;
}
#nav-mobile {
  font-family: @dop-font;
  letter-spacing: 0.9px !important;
}
.brand-logo {
  font-family: @dop-font;
  letter-spacing: 1px;
  font-size: 28px;
  color: #000;
  font-weight: 300;
  strong {
    font-weight: 600;
  }
}
.nav-li {
  color: #000;
  &:hover {
    background: #f0aca7;
  }
}
</style>
