<template>
  <div id="app">
    <div class="container">
      <div style="height: 20%">
        <Header @inputMethod="inputMethod"></Header>
      </div>
      <div style="height: 60%">
        <List ref="listRef" :inputVal="inputVal" @selectTotalMethod="selectTotalMethod"
          @rowTotalMethod="rowTotalMethod"></List>
      </div>
      <div style="height: 20%">
        <Footer :selectTotal="selectTotal" :rowTotal="rowTotal"></Footer>
        <el-button style="margin-right: 70px" @click="deleteClick" type="danger" size="mini">清除已完成任务</el-button>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";
export default {
  name: 'App',
  components: {
    Header,
    List,
    Footer
  },
  data() {
    return {
      inputVal: '',
      selectTotal: 0,
      rowTotal: 2
    }
  },
  methods: {
    inputMethod(val) {
      this.inputVal = val
    },
    selectTotalMethod(val) {
      this.selectTotal = val
    },
    rowTotalMethod(val) {
      this.rowTotal = val
    },
    deleteClick() {
      this.$refs.listRef.deleteData()
    }
    
  },
  
}
</script>

<style lang="less">
html,body,
#app {
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  height: 500px;
  width: 500px;
  background: #efefef;
  div {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
