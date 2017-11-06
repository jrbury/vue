<template>
  <div id="app">
    <div class='ui three column centered grid'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="addTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import swal from "sweetalert";
import TodoList from "./components/TodoList";
import CreateTodo from "./components/CreateTodo";

export default {
  name: "app",
  components: {
    TodoList,
    CreateTodo
  },
  data() {
    return {
      todos: [
        {
          title: "Todo A",
          project: "Project A",
          done: false
        },
        {
          title: "Todo B",
          project: "Project B",
          done: true
        },
        {
          title: "Todo C",
          project: "Project C",
          done: false
        },
        {
          title: "Todo D",
          project: "Project D",
          done: false
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      swal("Success!", "To-Do Added!", "success");
    }
  }
};
</script>

<style>

</style>
