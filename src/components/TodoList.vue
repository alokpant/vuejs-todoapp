<template>
  <section>
    <todo v-on:delete-todo="deleteTodoItem"
          v-for="todo in todos"
          v-bind:todo="todo"></todo>
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
      deleteTodoItem(toDelete) {
        const todoIndex = this.todos.indexOf(toDelete);
        this.todos.splice(todoIndex, 1);
      },
      addTodoItem(listToAdd) {
        this.todos.push(listToAdd)
      }
    }
  };
</script>

<style scoped>

</style>