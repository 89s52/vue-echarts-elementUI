<template>
<div id="app">
    <table>
        <thead>
        <tr>
            <th>姓名</th>
            <th>年龄</th>
            <th>住址</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="site in items">
            <td v-text="site.name"></td>
            <td v-text="site.age"></td>
            <td v-text="site.address"></td>
        </tr>
        </tbody>
    </table>
</div>
</template>
 
<script>
 
 
  export default {
    name: 'Demo05',
     data() {
            return {
             items:[{
  "name":"baby",
  "age":27,
  "address":"china weifang"
},
  {
    "name":"黄晓明",
    "age":30,
    "address":"china yantai"
  },
  {
    "name":"鹿晗",
    "age":22,
    "address":"china qingdao"
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
