<template>
  <div id="app">
    <Header />
    <add-todo v-on:addTodo="addTodo"></add-todo>
    <todos :todos="todos" v-on:del-todo=deleteTodo></todos>
  </div>
</template>

<script>

import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import Header from './components/layouts/Header'
export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
      console.log(id)
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo]
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
