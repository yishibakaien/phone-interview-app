<template>
  <div class="anwser-wrapper">
    <div
      class="anwser-item"
      v-for="(item, index) in anwser"
      :key="index"
      :data-scroe="item.score"
      @click="toggleActive"
    >
      {{item.desc}}
    </div>
  </div>
</template>
<script>
export default {
  props: {
    anwser: {
      type: Array
    }
  },
  methods: {
    toggleActive(ele) {
      // console.log(ele.target.className)
      let target = ele.target;
      let active = target.className.indexOf('active') !== -1;
      if (active) {
        target.className = target.className.replace(/\s*active\s*/g, '');
      } else {
        target.className += ' active';
      }
    }
  }
};
</script>
<style scoped>
.anwser-item {
  padding: 12px;
  border-radius: 4px;
  color: #666;
  background: #f3f3f3;
  margin-top: 8px;
  cursor: pointer;
}
.anwser-item.active {
  color: #609700;
  background: rgba(0, 255, 0, 0.1);
}
</style>
