<template>
  <div>
    <h2>{{ question.question }}</h2>
    <ul>
      <li v-for="choice in question.choices" :key="choice">
        <button @click="selectAnswer(choice)">{{ choice }}</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'QuizQuestion',
  props: ['question'],
  methods: {
    selectAnswer(choice) {
      const isCorrect = choice === this.question.correct;
      this.$emit('answer-selected', isCorrect);
    }
  }
};
</script>
