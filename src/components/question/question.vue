<template>
  <div class="question-wrapper">
    <!-- css部分 -->
    <h2 class="part">一、css 基础知识部分</h2>
    <div class="question-item" v-for="(item, index) in css" :key="index" :level="item.level">
      <div class="question-title">{{index + 1}}、{{item.question}}</div>
      <anwser :anwser="item.anwser"></anwser>
    </div>
    <!-- js 部分 -->
    <h2 class="part">二、javaScript 基础知识部分</h2>
    <div class="question-item" v-for="(item, index) in js" :key="'item_' + index" :level="item.level">
      <div class="question-title">{{index + 1}}、{{item.question}}</div>
      <anwser :anwser="item.anwser"></anwser>
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
      let items = document.querySelectorAll('.active');
      items = Array.from(items);
      let count = items
        .map(item => +item.getAttribute('data-scroe'))
        .reduce((pre, cur) => pre + cur, 0);
      alert('最终得分：' + count);
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
