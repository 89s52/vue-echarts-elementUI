<template>
<div id="app">
  <el-table
    :data="items"
    stripe
    style="width: 100%; height: 200px;">
    <el-table-column
      prop="date"
      label="日期"
      width="180">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="address"
      label="地址">
    </el-table-column>
  </el-table>
</div>
</template>
 
<script>
 
 
  export default {
    name: 'Demo05',
     data() {
            return {
           items: [{
          date: '2016-05-02',
          name: '张1狗',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '张2狗',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '张3狗',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '张4狗',
          address: '上海市普陀区金沙江路 1516 弄'
        }]
            }
        },
 
 
     

      created(){
                setInterval(this.scroll,5000)
            },


methods: {


    scroll(){
       setTimeout(()=>{      //  这里直接使用了es6的箭头函数，省去了处理this指向偏移问题，代码也比之前简化了很多
               this.items.push(this.items[0]);  // 将数组的第一个元素添加到数组的
               this.items.shift();               //删除数组的第一个元素,打印的是剩下的数组
       
       },500)
    }
}
 
  }
</script>
<style scoped>
        * {
            padding: 0;
            margin: 0;
        }

        table {
            width: 500px;
            height: 500px;
            margin: 100px auto;
            border: 1px solid #000;
            border-collapse: collapse; /*设置表格的边框是否被合并为一个单一的边框*/
            border-spacing: 0; /*设置相邻单元格的边框间的距离*/
        }

        tr {
            width: 300px;
            height: 50px;
            line-height: 50px;
            border-bottom: 1px solid #000;
            /*background-color: pink;*/
        }

        td, th {
            width: 40px;
            height: 40px;
            line-height: 40px;
            text-align: center;
            border-right: 1px solid #000;
        }

</style>
