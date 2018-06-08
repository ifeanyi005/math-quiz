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
          <transition name="flip" mode="out-in">
            <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-questions'"></component>
          </transition>
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


.flip-enter-active{
  animation: flip-in 0.5s ease-out forwards;
}


.flip-leave-active {
  animation: flip-out 0.5s ease-out forwards;
}

@keyframes flip-out {
  from {
    transform: rotateX(0deg)
  }
  to {
    transform: rotateX(90deg)
  }

}

@keyframes flip-in {
  from {
    transform: rotateX(90deg)
  }
  to {
    transform: rotateX(0deg)
  }
}
</style>
