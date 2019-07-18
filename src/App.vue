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
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id){

      axios.post(`https://jsonplaceholder.typicode.com/todos/${id}`,{
        title,
        completed
      })
      .then((response) => {
        this.todos = this.todos.filter(todo => todo.id !== id)
      })
      .catch(err => console.log(err))
    },
    addTodo(todo) {
      const { title, completed } = todo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
      .then((response) => {
        this.todos = [...this.todos, todo]
      })
      .catch(err => console.log(err))

    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then((response) => {
      this.todos = response.data
    })
    .catch(err => console.log(err))
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
