<template>
  <div class="hello">
    <question :data="questions.css"></question>
  </div>
</template>
<script>
import questions from '../questions'
import Question from './question/question'
export default {
  data () {
    return {
      questions: questions
    }
  },
  components: {
    Question
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
