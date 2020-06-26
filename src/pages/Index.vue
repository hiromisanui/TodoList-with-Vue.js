<template>
  <div>
    <h1>Todo List</h1>
    <todo-form @handleAddTodo="handleAddTodo" />
    <todo-list
      :todos="todos"
      @handleDeleteTodo="handleDeleteTodo"
      @handleCompleteTodo="handleCompleteTodo" />
  </div>
</template>

<script>
  import TodoForm from '@/components/TodoForm';
  import TodoList from '@/components/TodoList';

  export default {
    name: "Todo",
    components:{
      TodoForm,
      TodoList,
    },
    data(){
      return{
        todos:[],
      }
    },
    methods:{
      handleAddTodo(value){
        if(value){
          this.todos.unshift({text: value, complete: false});
        }
      },
      handleDeleteTodo(index){
        this.todos.splice(index, 1);
      },
      handleCompleteTodo(index){
        this.todos[index].complete = !this.todos[index].complete;
      }
    }
  }
</script>

<style scoped>
  h1{
    width: 200px;
    margin: 12px auto;
  }
</style>