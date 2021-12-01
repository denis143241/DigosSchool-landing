<template>
  <div class="card">
    <img :src="img" alt="" />
    <h3>
      {{ titleWithoutLastItem }}<span>{{ lastItem }}</span>
    </h3>
    <ul>
      <li v-for="text in addition" :key="text">{{ text }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    img: {
      require: true,
    },
    title: {
      type: String,
    },
    addition: {
      type: Array,
    },
  },
  computed: {
    titleWithoutLastItem() {
      let len = this.title.split(" ").length;
      return (
        this.title
          .split(" ")
          .slice(0, len - 1)
          .join(" ") + " "
      );
    },
    lastItem() {
      return this.title.split(" ")[this.title.split(" ").length - 1];
    },
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.card {
  box-shadow: none;
  margin: 40px 0 130px;
  font-family: @main-font;
}
img {
  width: 80px;
  height: 80px;
}
h3 {
  position: relative;
  font-size: 30px;
  font-weight: 700;
  margin-bottom: 50px;
}
span {
  position: relative;
  &::after {
    content: "";
    height: 5px;
    width: 100%;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #f17f77;
    border-radius: 50px;
  }
}
ul {
  max-width: 95%;
  font-family: @dop-font;
  letter-spacing: 0.9px;
}
li {
  font-size: 20px;
  color: @dop-color;
  position: relative;
  padding-left: 40px;
  &::before {
    content: "";
    width: 10px;
    height: 10px;
    background-color: #f1968f;
    border-radius: 50%;
    position: absolute;
    top: 10px;
    left: 5px;
  }
}
</style>
