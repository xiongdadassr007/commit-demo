<template>
  <div class="bottom" style="width: 100%">
    <div>
      <input type="checkbox" id="checkAll">
      <label for="checkAll">已完成 {{ selectTotal }} / 全部 {{ rowTotal }}</label>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'Footer',
  props: {
    selectTotal: {
      type: Number
    },
    rowTotal: {
      type: Number
    },
  }
}
</script>

<style lang="less" scoped>
 .bottom {
    display: flex;
    justify-content: space-around;
    width: 100%;
 }
</style>