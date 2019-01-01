<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1 class="text-center">The Super Quiz</h1>
            </div>
        </div>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <transition :name="answerTransition" mode="out-in">
                    <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
                </transition>
            </div>
        </div>
    </div>
</template>

<style>
    /* FADE */
    .fade-enter-active, .fade-leave-active {
    transition: opacity .1s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
    }

    /* BOUNCE */
    .bounce-enter-active {
    animation: bounce-in .5s;
    }
    .bounce-leave-active {
    animation: bounce-in .5s reverse;
    }
    @keyframes bounce-in {
        0% {
            transform: scale(0);
        }
        50% {
            transform: scale(1.5);
        }
        100% {
            transform: scale(1);
        }
    }
</style>

<script>
    import Question from './components/Question.vue';
    import Answer from './components/Answer.vue';
    import Wrong from './components/Wrong.vue';

    export default {
        data() {
            return {
                mode: 'app-question',
                answerTransition: 'bounce',
                showWrongAlert: false,
            }
        },
        methods: {
          answered(isCorrect) {
              if (isCorrect) {
                  this.answerTransition = 'bounce';
                  this.mode = 'app-answer';
              } else {
                  this.answerTransition = 'fade';
                  this.mode = 'app-wrong';
                //   alert('Wrong, try again!');
              }
          }
        },
        components: {
            appQuestion: Question,
            appAnswer: Answer,
            appWrong: Wrong,
        }
    }
</script>

