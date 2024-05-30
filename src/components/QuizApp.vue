<template>
  <div>
    <transition name="fade" mode="out-in">
      <QuizQuestion v-if="!quizCompleted" :key="currentQuestionIndex" :question="currentQuestion" @answer-selected="nextQuestion"/>
    </transition>
    <QuizResult v-if="quizCompleted" :score="score" :total="questions.length"/>
  </div>
</template>

<script>
import QuizQuestion from './QuizQuestion.vue';
import QuizResult from './QuizResult.vue';
import questions from '../data/questions.json';

export default {
  components: { QuizQuestion, QuizResult },
  data() {
    return {
      questions,
      currentQuestionIndex: 0,
      score: 0,
      quizCompleted: false
    };
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex];
    }
  },
  methods: {
    nextQuestion(isCorrect) {
      if (isCorrect) {
        this.score++;
      }
      this.currentQuestionIndex++;
      if (this.currentQuestionIndex >= this.questions.length) {
        this.quizCompleted = true;
      }
    }
  }
};
</script>
