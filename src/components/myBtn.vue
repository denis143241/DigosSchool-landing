<template>
  <div class="my-button">
    <button
      class="my-btn"
      :style="{
        backgroundColor: `#${color}`,
        backgroundImage: `url(${bg})`,
        backgroundSize: '100%',
        backgroundPosition: 'center center',
      }"
    >
      <slot />
    </button>
    <button
      class="my-btn back"
      :style="{
        border: `1px solid #${color}`,
        backgroundColor: `rgba(0,0,0,0)`,
      }"
    >
      "
    </button>
  </div>
</template>

<script>
export default {
  props: {
    color: {
      required: true,
      type: String,
    },
    bg: {
      required: false,
    },
    textColor: {
      type: String,
    },
  },
};
</script>

<style lang="less" scoped>
@keyframes on-hover {
  0% {
    top: 0;
    left: 0;
  }
  100% {
    top: 7px;
    left: 7px;
  }
}
.my-button {
  position: relative;
  color: #fff;
}
.my-btn {
  position: absolute;
  font-weight: 600;
  border: 1px solid rgba(0, 0, 0, 1);
  width: 85%;
  padding: 12px 20px;
  z-index: 20;
  transition: all 200ms;
  &:hover {
    animation: on-hover 200ms forwards;
  }
}
.back {
  position: absolute;
  top: 7px;
  left: 7px;
  z-index: 1;
  background-color: rgba(0, 0, 0, 0);
  &:hover {
    animation: none;
  }
}
</style>
