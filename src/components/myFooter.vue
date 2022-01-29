<template>
  <div class="parallax-container">
    <div ref="parallax" class="parallax">
      <img src="../assets/frame-footer.png" />
    </div>
    <div class="container">
      <div class="row footer-content wow fadeIn" data-wow-delay="300ms">
        <div class="col l3 m4 s6">
          <div class="subtitle">
            <div class="logo">DIGOSSCHOOL</div>
          </div>
          <ul>
            <li><a href="#">Преподавателям</a></li>
            <li><a href="#">Карьера в DIGOSSCHOOL</a></li>
            <li><a href="#">Отзывы</a></li>
            <li><a href="#">Адресса и телефоны</a></li>
            <li class="social hide-on-small-only"><social-media /></li>
          </ul>
        </div>
        <div class="col l3 m4 s6">
          <div class="subtitle">Обучение</div>
          <ul>
            <li><a href="#">Процесс</a></li>
            <li><a href="#">Курсы</a></li>
            <li><a href="#">Преподаватели</a></li>
            <li><a href="#">Вопрос-ответ</a></li>
            <li><a href="#">Подарить сертификат</a></li>
          </ul>
        </div>
        <div class="col l3 m4 s6">
          <div class="subtitle">Продукты</div>
          <ul>
            <li><a href="#">Онлайн образовательный портал</a></li>
          </ul>
        </div>
        <div class="col l3 m4 s6">
          <div class="subtitle">Дополнительно</div>
          <ul>
            <li><a href="#">Активация промокода</a></li>
            <li><a href="#">Тесты по английскому</a></li>
            <li><a href="#">Наши преподаватели</a></li>
            <li><a href="#">Цены</a></li>
          </ul>
        </div>
        <div class="col s8 offset-s2 hide-on-med-and-up"><social-media /></div>
      </div>
    </div>
  </div>
</template>

<script>
import socialMedia from "./socialMedia.vue";
export default {
  components: {
    socialMedia,
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.social {
  margin-top: 50px !important;
}
.footer-content {
  margin-top: 50px;
}
.parallax-container {
  height: 600px;
  color: #fff;
  font-size: 18px;
}
.logo {
  font-family: @dop-font;
  letter-spacing: 0.9px;
  font-weight: 500;
  font-size: 30px;
}
.subtitle {
  min-height: 100px;
  font-size: 20px;
  margin-top: 50px;
  display: flex;
  align-items: center;
  color: #eeeeee;
}
li {
  font-weight: 300;
  &:not(:last-child) {
    margin-bottom: 10px;
  }
}
a {
  font-family: @dop-font;
  letter-spacing: 0.8px;
  font-weight: 200;
  font-size: 18px;
  text-decoration: none;
  color: #fff;
  &:hover {
    text-decoration: underline;
  }
}
@media only screen and (max-width: 600px) {
  .parallax-container {
    height: 100%;
    font-size: 14px;
  }
  .subtitle {
    font-size: 18px;
  }
  .logo {
    font-size: 20px;
  }
  a {
    font-size: 16px;
  }
}
</style>
