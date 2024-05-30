<template>
  <div>
    <h2>Résultat du Quiz</h2>
    <p>Vous avez {{ score }} sur {{ total }}.</p>
  </div>
</template>

<script>
export default {
  name: 'QuizResult',
  props: ['score', 'total']
};
</script>
