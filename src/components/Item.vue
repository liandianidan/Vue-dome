<template>
  <li @mouseenter="handleEvent(true)"  @mouseleave="handleEvent(false)" 
  :style="{background:isColor}">
    <label>
    <input type="checkbox" v-model="todo.complete"/>
    <span>{{todo.title}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click="deletedItem">删除</button>
  </li>
</template>

<script type="text/ecmascript-6">
  export default {
      //接收并声明
      props:{
          todo:Object,
          deletedTodo:Function
      },
     data() {
        return{
            isColor:'#fff',
            isShow:false
        }
     },
     methods:{
         //鼠标移入移出的按钮显示设置
         handleEvent(isEnter) {
            if(isEnter){
             this.isColor='#eee'
             this.isShow=true
            }else{
             this.isColor='#fff'
             this.isShow=false
            }
         },
         //删除每一项的方法
         deletedItem() {
            if(confirm('确认删除吗？')){
                //父组件定义函数，子组件调用并传参
               this.deletedTodo(this.index)
            }
         }
     }
  }
</script>

<style scoped>
    /*item*/
    li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
    }

    li label {
    float: left;
    cursor: pointer;
    }

    li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
    }

    li button {
    float: right;
    margin-top: 3px;
    }

    li:before {
    content: initial;
    }

    li:last-child {
    border-bottom: none;
    }
 
</style>
