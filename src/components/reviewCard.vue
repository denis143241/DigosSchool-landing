<template>
  <div class="card">
    <p id="text">
      Отличная школа!<br />
      Очень удобный формат обучения! Сам выбираешь время, которое тебе удобно,
      сам выбираешь преподавателя по их резюме и записи голосового резюме на
      английском. Интересные упражнения и домашнее задание
    </p>
    <img src="../assets/customer-2.jpg" alt="" />
    <p class="name">Denis Igoshin</p>
    <p class="description">Фронтенд-разработчик</p>
  </div>
</template>

<style lang="less" scoped>
img {
  width: 110px;
  height: 110px;
  margin: 20px 0;
  border-radius: 100%;
}
.card {
  width: 310px;
  min-height: 430px;
  padding: 25px;
  display: flex;
  flex-direction: column;
  border-radius: 3%;
}
#text {
  flex-grow: 1;
}
p {
  margin: 0;
}
.name,
.description {
  padding-bottom: 7px;
}
.name {
  position: relative;
  font-weight: 900;
  font-size: 16px;
  &::after {
    content: "";
    width: 30px;
    height: 5px;
    background-color: #f17f77;
    position: absolute;
    top: 100%;
    left: 15%;
    border-radius: 50px;
  }
}
.description {
  margin-top: 10px;
}
</style>
