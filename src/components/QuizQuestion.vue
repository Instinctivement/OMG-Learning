<template>
  <div>
    <h2>{{ question.question }}</h2>
    <ul>
      <li v-for="(choice, index) in question.choices" :key="index">
        <label>
          <input type="checkbox" :value="index" v-model="selectedAnswers">
          {{ choice }}
        </label>
      </li>
    </ul>
    <button @click="submitAnswer">Submit Answer</button>
  </div>
</template>

<script>
export default {
  name: 'QuizQuestion',
  props: ['question'],
  data() {
    return {
      selectedAnswers: []  // Track selected answers for multi-selection
    };
  },
  methods: {
    submitAnswer() {
      const sortedSelectedAnswers = [...this.selectedAnswers].sort();
      const sortedCorrectAnswers = [...this.question.correct].sort();
      const isCorrect = JSON.stringify(sortedSelectedAnswers) === JSON.stringify(sortedCorrectAnswers);
      this.$emit('answer-selected', isCorrect, this.question.explanation);
      this.selectedAnswers = []; // Reset after submitting
    }
  }
};
</script>
