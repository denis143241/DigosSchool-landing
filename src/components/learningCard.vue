<template>
  <div class="card">
    <div class="card-image waves-effect waves-block waves-light">
      <img class="activator" :src="image" />
    </div>
    <div class="card-content">
      <span class="card-title activator grey-text text-darken-4"
        ><slot name="title" />
        <i class="material-icons right">more_vert</i></span
      >
    </div>
    <div class="card-reveal">
      <span class="card-title grey-text text-darken-4"
        ><slot name="title" /><i class="material-icons right">close</i></span
      >
      <p>
        <slot name="text" />
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    image: {
      required: true,
      title: {
        required: true,
      },
    },
  },
};
</script>

<style lang="less" scoped>
@import url("../assets/mainStyle.less");
.card {
  max-width: 500px;
  
  font-family: @dop-font;
  letter-spacing: 0.9;
  &:hover {
    box-shadow: 0 0 20px #f17f77;
  }
}
</style>
