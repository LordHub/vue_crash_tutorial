<template>
    <div class="todo-item" :class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" @change="markComplete">
            {{todo.title}}
            <button class="del" @click="$emit('del-todo', todo.id)">x</button>
        </p>
    </div>
</template>

<script>
  export default {
    name: "TodoItem",
    props: ['todo'],
    methods: {
      markComplete(){
        this.todo.completed = !this.todo.completed
      }
    }
  }
</script>

<style scoped>
  .todo-item{
    background: aquamarine;
    padding: 10px;
    border-bottom: 1px #ffffff dashed;
  }
  .is-complete {
     background: green;
      text-decoration: line-through;
  }
</style>