<template>
  <div class="main-title wow fadeInUp">
    <slot />
  </div>
</template>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.main-title {
  font-family: @main-font;
  letter-spacing: 1px;
  font-weight: 700;
  text-transform: inherit;
  text-align: center;
  font-size: 40px;
  margin: 20px 0 40px;
}
</style>
