<template>
  <div class="card">
    <div class="container">
      <div class="row flex-row">
        <div class="col m4">
          <img :src="img" alt="" />
        </div>
        <div class="col m8 title">
          <h3>{{ title }}</h3>
        </div>
      </div>
      <ul>
        <li v-for="text in addition" :key="text">{{ text }}</li>
      </ul>
    </div>
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
};
</script>

<style lang="less" scoped>
.card {
  min-height: 300px;
}
img {
  width: 60px;
  height: 60px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 0;
}
h3 {
  margin: 0;
  padding: 0;
  font-size: 26px;
}
.flex-row {
  position: relative;
  padding: 40px 0;
}
ul {
  margin: 0 20px;
}
li {
  font-size: 14px;
  position: relative;
  padding-left: 8px;
  &::before {
    content: "";
    width: 10px;
    height: 10px;
    background-color: #f1968f;
    border-radius: 50%;
    position: absolute;
    top: 6px;
    left: -20px;
  }
}
.title {
  padding: 0;
}
</style>
