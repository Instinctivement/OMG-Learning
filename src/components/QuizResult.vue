<template>
  <div>
    <h2>Résultat du Quiz</h2>
    <p>Vous avez {{ score }} sur {{ total }}.</p>
    <ul>
      <li v-for="(detail, index) in details" :key="index">
        <p>Question {{ index + 1 }}: {{ detail.explanation }}</p>
        <p v-if="detail.isCorrect">Correct</p>
        <p v-else>Incorrect</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'QuizResult',
  props: ['score', 'total', 'details']
};
</script>
