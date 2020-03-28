<template>
  <div class="question-box-container">
    <b-jumbotron>
      <template v-slot:lead>
       Some question here?
      </template>

      <hr class="my-4">

      <p>
        List of answers
      </p>

      <b-button variant="primary" href="#" class="m-2">Submit</b-button>
      <b-button variant="success" href="#" class="m-2">Next</b-button>
    </b-jumbotron>
  </div>
</template>