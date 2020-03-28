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
  export default {
    props: {
      currentQuestion: Object,
      next: Function
    },
    computed: {
      answers() {
        const answers  = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
        return answers;
      }
    }
  }
</script>