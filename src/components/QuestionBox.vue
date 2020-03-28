<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template v-slot:lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4">

      <b-list-group>
        <b-list-group-item
          v-for="(answer, index) in answers"
          :key="index"
          @click="selectAnswer(index)"
          :class="[selectedIndex === index ? 'selected' : '']"
        >
          {{ answer }}
        </b-list-group-item>
      </b-list-group>

      <b-button variant="primary" href="#" class="m-4">Submit</b-button>
      <b-button @click="next" variant="success" href="#" class="m-2">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
  import _ from 'lodash';

  export default {
    props: {
      currentQuestion: Object,
      next: Function
    },
    data() {
      return {
        selectedIndex: null,
        shuffledAnswers: []
      }
    },
    computed: {
      answers() {
        const answers  = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
        return answers;
      }
    },
    watch: {
      currentQuestion: {
        immediate: true,
        handler() {
          this.selectedIndex = null;
          this.shuffleAnswers();
        }
      }
    },
    methods: {
      selectAnswer(index) {
        this.selectedIndex = index;
      },
      shuffleAnswers() {
        const answers  = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
        this.shuffledAnswers = _.shuffle(answers);
      }
    }
  }
</script>

<style scoped>
  .list-group-item:hover {
    background-color: #eee;
    cursor: pointer;
  }
  .selected {
    background-color: lightblue;
  }
  .correct {
    background-color: lightgreen;
  }
  .incorrect {
    background-color: lightsalmon;
  }
</style>