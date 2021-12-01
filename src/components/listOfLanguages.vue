<template>
  <div class="row">
    <div v-for="lang in contries" :key="lang" :class="`col m${size}`">
      <div
        class="flag"
        :style="{
          background: `url(${lang.flag}) no-repeat center center`,
          backgroundSize: '100%',
        }"
        :class="{ checked: lang.checked }"
        @click="setCheck(lang)"
      ></div>
      <h6>{{ lang.text }}</h6>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    size: {},
  },
  data() {
    return {
      contries: [
        {
          text: "Английский",
          flag: require("../assets/britainForBtn.png"),
          checked: false,
        },
        {
          text: "Испанский",
          flag: require("../assets/spainForBtn.png"),
          checked: false,
        },
        {
          text: "Итальянский",
          flag: require("../assets/italyForBtn3.png"),
          checked: false,
        },
        {
          text: "Французский",
          flag: require("../assets/franceForBtn.png"),
          checked: false,
        },
        {
          text: "Немецкий",
          flag: require("../assets/germanyForBtn1.png"),
          checked: false,
        },
      ],
    };
  },
  methods: {
    setBase() {
      this.contries.forEach((c) => (c.checked = false));
    },
    setCheck(country) {
      this.setBase();
      country.checked = true;
      this.$emit("stateLang", { lang: country.text });
    },
  },
};
</script>

<style lang="less" scoped>
.flag {
  width: 100%;
  height: 50px;
  transition: 0.2s;
  &:hover {
    box-shadow: 0 0 20px #f17f77;
    transform: scale(1.025);
    cursor: pointer;
  }
}
h6 {
  text-align: center;
  margin-top: 20px;
  margin-bottom: 40px;
}
.checked {
  box-shadow: 0 0 20px #f17f77;
  transform: scale(1.025);
}
</style>
