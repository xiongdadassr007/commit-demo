<template>
    <div>
      <input type="text" 
        placeholder="请输入您的任务名称，按回车键确认" 
        v-model="inputData"
        @keyup.enter="handerSearch">
    </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      inputData: ''
    }
  },
  methods: {
    handerSearch() {
      this.$emit('inputMethod', this.inputData)
      this.inputData = ''
    }
  } 
}
</script>

<style lang="less" scoped>
input {
  width: 300px;
  height: 30px;
}
</style>