<template>
  <div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="title"
         @keyup.enter="add"/>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props:{
      addTodo:Function
    },
     data() {
         return{
         //初始值是空的
         title:''
         }
     },
     methods:{
         add(){
             //根据输入的数据准备一个todo
             //去除空格
            let title = this.title.trim() 
            //判断有没有输入
            if(!title){
                alert('请先输入内容')
                return
            }
            //创建数据
            const todo={
                id:Date.now(),
                complete:false,
                title
            }
             //向数据里添加一个todo
             //在父组件里定义一个方法，子组件调用并传参
            this.addTodo(todo)
             //清空input框
             this.title=''
         }
     }
  }
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}
 
</style>
