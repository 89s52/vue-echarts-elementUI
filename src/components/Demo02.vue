<template>
<div class="vueBox" >
    <div class="marquee">
        <div class="marquee_title">
        
        </div>
        <div class="marquee_box">
            <ul class="marquee_list" :style="{ top: -num + 'px'}" :class="{marquee_top:num}">
            <!-- 当显示最后一条的时候（num=0转换布尔类型为false）去掉过渡效果-->
                作者：ID
                <li v-for="(item, index) in items"    >
                   <span class="red">  {{item.author_id}} {{item.id}}</span>
                </li>
            </ul>
        </div>
    </div>
</div>
</template>
 
<script>
 
 
  export default {
    name: 'Demo05',
     data() {
            return {
                items: [
    
                ]
            }
        },
 
 
      created(){
                setInterval(this.getData,5000)
            },

      mounted(){
                setInterval(this.scroll,5000)
            },


methods: {

    getData () {
      this.$api.get('topics', null, r => {
        this.items = r.data
        console.log("结果"+r.data);
      })
    },

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
 div,ul,li,span,img{
            margin:0;
            padding:0;
            display: flex;
            box-sizing: border-box;
        }
        .marquee{
            width: 100%;
            height: 600px;
            align-items: center;
            color: #6f8498;
            /*background-color: aqua;*/
            display: flex;
            box-sizing: border-box;
        }
        .marquee_title{
            padding: 0 20px;
            height: 30px;/*关键样式*/
            font-size: 14px;
            border-right: 1px solid #d8d8d8;
            align-items: center;
        }
 
        .marquee_box{
            display: block;
            position: relative;
            width: 1200px;/*关键样式*/
            height: 500px;/*关键样式*/
            overflow: hidden;
              color:black;
        }
        .marquee_list{
            display: block;
            position: absolute;
            top:0;
            left: 0;
        }
        .marquee_top{transition: top 0.5s ;}/*关键样式*/
        .marquee_list li{
            height: 30px;/*关键样式*/
            line-height: 30px;/*关键样式*/
            font-size: 24px;
            padding-left: 20px;
            background-color: #fff;
        }
        .marquee_list li span{
            padding:0 2px;
        }
        .red{
            color: #FF0101;
        }
</style>
