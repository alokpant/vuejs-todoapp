<template>
  <section>
    <todo v-on:delete-todo="deleteTodoItem"
          v-for="todo in todos"
          v-bind:todo="todo"
          v-on:completed-todo="completeTodo"
          :todo.sync="todo"></todo>
    <create-todo v-on:create-todo="addTodoItem"></create-todo>
  </section>
</template>

<script type="text/javascript">
  import Todo from './Todo';
  import CreateTodo from './CreateTodo';
  
  export default {
    props: ['todos'],
    components: {
      Todo,
      CreateTodo,
    },
    methods: {
      getIndexOnTodo(item) {
        return this.todos.indexOf(item);
      },
      deleteTodoItem(toDelete) {
        this.todos.splice(this.getIndexOnTodo(toDelete), 1);
      },
      addTodoItem(listToAdd) {
        this.todos.push(listToAdd)
      },
      completeTodo(listToComplete) {
        this.todos[this.getIndexOnTodo(listToComplete)].done = true;
      }
    }
  };
</script>

<style scoped>

</style>