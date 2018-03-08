<template>
  <div class="question-wrapper">
    <!-- css部分 -->
    <div class="css-container">
      <h2 class="part">一、css 基础知识部分</h2>
      <div class="question-item" v-for="(item, index) in css" :key="index" :level="item.level">
        <div class="question-title">{{index + 1}}、{{item.question}}</div>
        <anwser :anwser="item.anwser"></anwser>
      </div>
    </div>

    <!-- js 部分 -->
    <div class="js-container">
      <h2 class="part">二、javaScript 基础知识部分</h2>
      <div class="question-item" v-for="(item, index) in js" :key="'item_' + index" :level="item.level">
        <div class="question-title">{{index + 1}}、{{item.question}}</div>
        <anwser :anwser="item.anwser"></anwser>
      </div>
    </div>

    <button class="button" @click="count">计算得分</button>
  </div>
</template>
<script>
import Anwser from './anwser';
import questions from '../../questions';
export default {
  props: {
    question: {
      type: Array
    }
  },
  data() {
    return {
      js: questions.js,
      css: questions.css
    };
  },
  methods: {
    count() {
      let cssItems = document.querySelectorAll('.css-container .anwser-item');
      cssItems = Array.from(cssItems);

      let jsItems = document.querySelectorAll('.js-container .anwser-item');
      jsItems = Array.from(jsItems);

      let cssCount = cssItems
        .map(item => {
          if (item.className.indexOf('active') !== -1) {
            return item.getAttribute('data-score');
          } else {
            return '0';
          }
        })
        .join('');
      let cssScore = cssCount
        .split('')
        .map(item => +item)
        .reduce((pre, cur) => pre + cur, 0);

      let jsCount = jsItems
        .map(item => {
          if (item.className.indexOf('active') !== -1) {
            return item.getAttribute('data-score');
          } else {
            return '0';
          }
        })
        .join('');
      let jsScore = jsCount
        .split('')
        .map(item => +item)
        .reduce((pre, cur) => pre + cur, 0);

      let totalScore = Array.from(document.querySelectorAll('.anwser-item'))
        .map(item => +item.getAttribute('data-score'))
        .reduce((pre, cur) => pre + cur, 0);

      console.log('totalScore', totalScore);

      let result = (cssScore + jsScore) / totalScore;
      result = result * 100;
      result = Math.round(result);
      alert(`最终得分：${cssCount}/${jsCount}/(${result})`);
    }
  },
  components: {
    Anwser
  }
};
</script>

<style>
.part {
  font-size: 20px;
  line-height: 2;
  margin-top: 16px;
}
.question-wrapper .question-item {
  box-sizing: border-box;
  padding: 16px;
  border: 1px dashed rgba(7, 17, 27, 0.2);
  margin-bottom: 16px;
  /*box-shadow: 3px 3px 10px rgba(7, 17, 27, 0.1);*/
}
.question-title {
  font-weight: 500;
}
.button {
  display: block;
  padding: 0 4px;
  line-height: 2;
  font-size: 20px;
}
</style>
