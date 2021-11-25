<template>
  <div class="social-block">
    <div class="social">
      <a href="#"><img src="../assets/social/vk.png" alt="" /></a>
    </div>
    <div class="social">
      <a href="#"><img src="../assets/social/telegram.png" alt="" /></a>
    </div>
    <div class="social">
      <a href="#"><img src="../assets/social/twitter.png" alt="" /></a>
    </div>
    <div class="social">
      <a href="#"><img src="../assets/social/whatsapp.png" alt="" /></a>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="less" scoped>
.social-block {
  display: flex;
  margin: 30px 0;
}
.social {
  width: 40px;
  height: 40px;
  transition: 0.2s;
  &:not(:first-child) {
    margin-left: 15px;
  }
  &:hover {
    transform: scale(1.1);
  }
}
img {
  width: 100%;
  height: 100%;
}
</style>
