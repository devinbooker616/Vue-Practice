<template>
  <div id="app">
    <Nav class="mb-6" />
    <Header />

    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuestionBox from "./components/QuestionBox.vue";
import Nav from "./components/Nav.vue";

export default {
  name: "App",
  components: {
    Nav,
    Header,
    QuestionBox,
  },
  data() {
    return {
      question: [],
    };
  },
  mounted: function() {
    fetch("https://opentdb.com/api.php?amount=10&category=9&type=multiple", {
      method: "get",
    })
      .then((response) => {
        return response.json();
      })
      .then((jsonData) => {
        this.question = jsonData.results;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
