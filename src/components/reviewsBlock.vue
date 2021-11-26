<template>
  <div class="full-block">
    <div class="parallax-container">
      <div ref="parallax" class="parallax">
        <!-- <img src="../assets/sky-short.jpg" /> -->
        <img src="../assets/frame-2new.png" alt="">
      </div>
    </div>
    <div class="container absolute-container">
      <h4>Что говорят наши<br />выпускники?</h4>
      <div class="cards">
        <review-card class="my-card"></review-card>
        <review-card class="my-card"></review-card>
        <review-card class="my-card"></review-card>
      </div>
    </div>
  </div>
</template>

<!-- <div class="container">
    <div class="full-block">
      <div class="parallax-container">
        <div ref="parallax" class="parallax">
          <img src="../assets/sky-short.jpg" />
        </div>
        <h4>Что говорят наши<br />выпускники?</h4>
      </div>
      <div class="absolute-container">
        <div class="cards">
          <review-card class="my-card"></review-card>
          <review-card class="my-card"></review-card>
          <review-card class="my-card"></review-card>
        </div>
      </div>
    </div>
  </div> -->

<script>
import reviewCard from "./reviewCard.vue";
export default {
  components: {
    reviewCard,
  },
};
</script>

<style lang="less" scoped>
.full-block {
  position: relative;
  width: 100%;
  margin-bottom: 300px;
}
.parallax-container {
  height: 500px;
  margin: 0 auto;
  border-radius: 20px;
  width: 90%;
}
.absolute-container {
  position: absolute;
  top: 0;
  z-index: 2;
  left: 50%;
  transform: translateX(-50%);
}
.cards {
  display: flex;
  width: 100%;
  justify-content: space-around;
  margin: 100px auto 0 0;
}
h4 {
  color: #fff;
  font-weight: 500;
  font-size: 50px;
  margin-top: 50px;
  // margin-left: 30px;
}
</style>
