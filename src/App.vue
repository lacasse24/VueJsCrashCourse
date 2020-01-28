<template>
  <div id="app">
    <Header/>
  <AddTodo v-on:add-todo="addTodo" />
  <Todos v-bind:todosProps="todos" v-on:del-todo="deleteTodo"/>
   
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
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
  //created is outside of methods: because it's part of the Vue life-cycle
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data);
    },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
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
