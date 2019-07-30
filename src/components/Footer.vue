<template>
   <div class="todo-footer">
        <label>
          <input type="checkbox" v-model="checkAll"/>
        </label>
        <span>
          <span>已完成{{completeCount}}</span> / 全部{{todos.length}}
        </span>
        <button class="btn btn-danger" v-if="completeCount>0" @click="deleteComplear">清除已完成任务</button>
      </div>
</template>

<script type="text/ecmascript-6">
  export default {
      //获取并声明
     props:{
        todos:Array,
        selectAll:Function,
        deleteComplear:Function
        
      },
     
      //计算属性
      computed:{
       //选中的个数，用数组的累加方法如果todo.complete是true就加一，如果是false就加0
        completeCount(){
            return this.todos.reduce((pre,todo)=>pre+(todo.complete?1:0),0)
        },
      
        //当都选中时他就选中，有一个没有选中，他也没有选中，都不选他也不选
        checkAll:{
            get(){
               return this.completeCount===this.todos.length && this.completeCount>0
            },
            set(value){//监视总的复选框，如果勾选上，就都选
               this.selectAll(value)
            }
          
        }
      }
     
  }
 
</script>

<style scoped>
    /*footer*/
    .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
    }

    .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
    }

    .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
    }

    .todo-footer button {
    float: right;
    margin-top: 5px;
    }
 
</style>
