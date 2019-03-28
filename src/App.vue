<template>
  <div id="app">
    <Header :numCorrect="numCorrect" :numTotal="numtotal"/>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            v-if="questions.length"
            :currentQuestion="questions[index]"
            :next="next"
            :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuestionBox from "./components/QuestionBox.vue";

export default {
  name: "app",
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numtotal: 0
    };
  },
  mounted() {
    fetch("https://opentdb.com/api.php?amount=10&category=27&type=multiple", {
      method: "get"
    })
      .then(response => {
        return response.json();
      })
      .then(data => {
        this.questions = data.results;
      });
  },
  methods: {
    next() {
      this.index = this.index + 1;
    },
    increment(isCorrect) {
      if (isCorrect) {
        this.numCorrect++;
      }
      this.numtotal++;
    }
  },
  components: {
    Header,
    QuestionBox
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
