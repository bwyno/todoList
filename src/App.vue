<script>
//import HelloWorld from './components/HelloWorld.vue'
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'
export default {
  components: {
    TodoForm,
    TodoList
  }, 
  data () {
    return {
      todoItems: []
    }
  },
  methods: {
    addTodo (todo) {
      this.todoItems.push(todo);
    }
  }
}

</script>

<template>
    <div class="main-body-flex  ">

      <div class="header">
        <header>
        <h1>To-do List</h1>
        </header>
      </div>
      <div class="todo-form">
        <TodoForm @todo-submitted="addTodo"></TodoForm>
      </div>
      <div class="todo-list">
        <TodoList v-if="todoItems.length" :todoItems="todoItems"></TodoList>  
      </div>
      
    </div>

</template>

<style scoped>

.main-body-flex {
  display: flex;
  flex-direction: column;
}

.header {
  text-align: center;
  margin-bottom: 50px;
}

.todo-form {
  margin: auto;
}

.todo-list {
  margin: auto;
  margin-top: 50px;
}

</style>

