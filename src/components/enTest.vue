<template>
  <div class="questions">
    <div class="title">{{ questions[cnt].question }}</div>
    <div class="block-answers">
      <span
        @click="next(ans)"
        v-for="(ans, idx) in questions[cnt].answers"
        :key="idx"
        >{{ ans }}</span
      >
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cnt: 0,
      score: 0,
      questions: [
        {
          question: "There are ... roses in ... garden",
          answers: ["... , the", "the , the", "... , a"],
          correct: "... , the",
        },
        {
          question: "... you OK? Yes, I ...",
          answers: ["are , am", "are , are", "is , am"],
          correct: "are , am",
        },
        {
          question:
            "Stop ... time browsing the Internet and tidy up your room at last!",
          answers: ["wasted", "to waste", "wasting"],
          correct: "wasting",
        },
        {
          question: "This church ... in the 17th century",
          answers: ["was build", "had built", "have built"],
          correct: "had built",
        },
        {
          question:
            "Don't blame everything ... your parents. You should be responsible for your decisions.",
          answers: ["on", "for", "of", "in"],
          correct: "on",
        },
        {
          question: "I ... understand you.",
          answers: ["am not", "can't", "may"],
          correct: "can't",
        },
        {
          question: "They usually go to school ... bus",
          answers: ["on", "in", "by"],
          correct: "by",
        },
        {
          question: "This apple is ... than a candy!",
          answers: ["the sweetest", "sweeter", "the sweeter"],
          correct: "sweeter",
        },
        {
          question: "I would draw a picture if I ... any paints.",
          answers: ["had", "would have", "will be"],
          correct: "had",
        },
        {
          question: "My greatest ... in life is my business.",
          answers: ["achievely", "achievement", "unachievable"],
          correct: "achievement",
        },
      ],
    };
  },
  methods: {
    next(item) {
      if (this.cnt >= this.questions.length - 1) {
        this.$emit("end", {
          score: this.score,
        });
        return;
      }
      if (item === this.questions[this.cnt].correct) {
        this.score++;
      }
      this.cnt++;
    },
  },
};
</script>

<style lang="less" scoped>
.next {
  margin: 80px auto;
  width: 200px;
}
.questions {
  text-align: center;
}
.title {
  font-size: 30px;
  font-weight: 700;
  margin-bottom: 80px;
}
span {
  padding: 10px 20px;
  background: #e0e0e0;
  position: relative;
  &:not(:first-child) {
    margin-left: 20px;
  }
  &::after {
    content: "";
    height: 5px;
    width: 100%;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #f17f77;
    border-radius: 50px;
    opacity: 0;
  }
  &:hover {
    cursor: pointer;
  }
  &:hover::after {
    opacity: 1;
  }
}
</style>
