<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <h1 class="title">淘宝新制造-外包人员第一轮电话面试题目</h1>
    <div>tip: 点击答案，绿色背景表示回答正确</div>
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App'
};
</script>

<style>
.title {
  font-size: 24px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.6;
  /*text-align: center;*/
  padding: 16px;
  color: #333;
}
</style>
