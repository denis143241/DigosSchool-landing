<template>
  <div class="card">
    <p id="text">
      {{ person.text }}
    </p>
    <img :src="person.img" alt="" />
    <p class="name">{{ person.name }}</p>
    <p class="description">{{ person.work }}</p>
  </div>
</template>

<script>
export default {
  props: {
    person: {
      type: Object,
    },
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
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
  font-family: @dop-font;
  letter-spacing: .8px;
  color: @dop-color;
}
p {
  margin: 0;
}
.name,
.description {
  padding-bottom: 7px;
}
.name {
  font-family: @main-font;
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
  font-family: @dop-font;
  color: @dop-color;
  letter-spacing: .9px;
  margin-top: 10px;
}
</style>
