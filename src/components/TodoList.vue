<template>
  <div class="ui centered">
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

    <todo 
      v-on:delete-todo="deleteTodo"
      v-on:complete-todo="completeTodo"
      v-for="(todo, index) in todos" 
      v-bind:todo="todo" 
      :key="index">
    </todo>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  props: ["todos"],
  components: {
    Todo
  },
  methods: {
    deleteTodo(todo) {
      swal({
        title: "Are you sure?",
        text: "Confirm to delete the To-Do",
        icon: "warning",
        buttons: true,
        dangerMode: true
      }).then(willDelete => {
        if (willDelete) {
          const todoIndex = this.todos.indexOf(todo);
          this.todos.splice(todoIndex, 1);
          swal({ text: "Successfully deleted todo!", icon: "success" });
        }
      });
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    }
  }
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>

