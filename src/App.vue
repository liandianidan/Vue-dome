<template>
    <div class="todo-container">
      <div class="todo-wrap">
        <Header :addTodo="addTodo"></Header>
        <List :todos="todos" :deletedTodo="deletedTodo"></List>
        <Footer :todos="todos" :selectAll="selectAll" :deleteComplear="deleteComplear"></Footer>
    </div>
  </div>
</template>
 <script >
    import Header from './components/Header.vue'
    import List from './components/List.vue'
    import Footer from './components/Footer.vue'
      export default {
          data() {
            return{
               todos: [
               {id:1,title:'吃饭',complete:false},
               {id:2,title:'睡觉',complete:true},
               {id:3,title:'刷抖音',complete:false},
             ]
            }
          },
          methods: {
            //添加一个列表
            addTodo(todo) {
              this.todos.unshift(todo)
            },
            //删除一个列表
            deletedTodo(index){
              this.todos.splice(index,1)
            },
           
            //全选/ 全不选。遍历每一项，让每一项的complete都等于用户点击的
            selectAll(isCheck){
               this.todos.forEach(todo=>todo.complete=isCheck)
            },
             //删除已完成 filter返回值是个布尔值  过滤掉已选择的，留下未选择的
            deleteComplear(){
              this.todos=this.todos.filter(todo=>!todo.complete)
              
            },
          },
       components:{
          Header,
          List,
          Footer
       }
      }
</script>
<style scoped>
/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}


</style>
