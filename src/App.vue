<template>
  <div class="container">
    <div class="row">
      <div class="col-8 offset-2">
        <h1 class="text-center">A super quiz game</h1>
        <hr>

      </div>
    </div>
        <div class="row">
      <div class="col-8 offset-2">
         <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-questions'"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Answers from './components/Answers'
import Questions from './components/Questions'
export default {
  data() {
    return {
      mode: 'app-questions'
    }
  },
  methods: {
          answered(isCorrect) {
              if (isCorrect) {
                  this.mode = 'app-answers';
              } else {
                  this.mode = 'app-questions';
                  alert('Wrong, try again!');
              }
          }
        },
  components: {
    appAnswers: Answers,
    appQuestions: Questions
  }
}
</script>

<style>

</style>
