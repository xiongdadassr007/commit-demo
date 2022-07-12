<template>
  <div>
    <el-table ref="multipleTable" :data="tableData" tooltip-effect="dark" @selection-change="handleSelectionChange"
      :show-header="false" @cell-mouse-enter="mouseEnter" @cell-mouse-leave="mouseLeave" @select="select"
      :row-class-name="tableRowClassName">
      <el-table-column type="selection" width="55">
      </el-table-column>
      <el-table-column label="日期" width="300">
        <template slot-scope="scope">{{ scope.row.date }}</template>
      </el-table-column>
      <el-table-column align="right">
        <template slot-scope="scope">
          <el-button v-show="scope.row.showIcon" size="mini" type="danger"
            @click="handleDelete(scope.$index, tableData)">Delete
          </el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    inputVal: {
      type: String
    }
  },
  data() {
        return {
          multipleSelection: [],
          isShow: false,
          tableData: [
            {
              date: 'xxxx',
            }, {
              date: 'yyyy',
            },
          ],
          selectionItemIndexes: []
        }
  },
  computed: {
    rowTotal() {
      return this.tableData.length
    }
  },
  methods: {
    handleSelectionChange(val) {
      console.log(222, val);
      this.multipleSelection = val;
      this.selectionItemIndexes = [];
      val.forEach(item => {
        this.selectionItemIndexes.push(item.index)
      })
    },
    select(td) {
      this.$emit('selectTotalMethod', td.length)
      console.log(this.tableData.length);
    },
    handleDelete(index, rows) {
      rows.splice(index, 1)
    },
    mouseEnter(row, column, cell, event) {
      // console.log(222, row, column, cell, event);
      row.showIcon = true
      // console.log(777, this.rowTotal);
    },
    mouseLeave(row) {
      row.showIcon = false
    },
    init() {
      const list = []
      this.tableData.forEach((item) => {
        list.push({ ...item, showIcon : false })
      })
      this.tableData = list
    },
    tableRowClassName(row, index) {
      // console.log(row);
      row.row.index = row.rowIndex
    },
    deleteData() {
      this.tableData = this.tableData.filter((item, index) => {
        let arrlist = this.selectionItemIndexes
        return !arrlist.includes(index)
      })
    }
   
  },
  created() {
    this.init();
  },
  watch: {
    inputVal(newVal, oldVal){
      // console.log(222, newVal, oldVal);
      let demo = [{
        date: newVal,
        showIcon: false
      }]
      this.tableData = [...this.tableData, ...demo]
    },
    rowTotal(newVal, oldVal) {
      // console.log(11111, newVal);
      this.$emit('rowTotalMethod', newVal)
    }
    
  }
  
  
}
</script>

<style>

</style>