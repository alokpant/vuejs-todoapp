<template>
  <section>
    <todo v-on:delete-todo="deleteTodoItem"
          v-for="todo in todos"
          v-bind:todo="todo"></todo>
  </section>
</template>

<script type="text/javascript">
  import Todo from './Todo';
  
  export default {
    props: ['todos'],
    components: {
      Todo,
    },
    methods: {
      deleteTodoItem(toDelete) {
        const todoIndex = this.todos.indexOf(toDelete);
        this.todos.splice(todoIndex, 1);
      }
    }
  };
</script>

<style scoped>

</style>