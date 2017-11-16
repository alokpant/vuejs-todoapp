<template>
  <section>
    <div class="ui centered card" v-if="isNotEditMode">
      <div class='content'>
        <div class='header'>
          {{ todo.title }}
        </div>
        <div class='meta'>
          {{ todo.project }}
        </div>
        <div class='extra content'>
          <button class="ui labeled icon button" v-on:click="showEditForm">
            <i class="edit icon"></i>
            Edit
          </button>
          <button class="ui labeled icon button" v-on:click="deleteForm(todo)">
            <i class="delete icon"></i>
            Delete
          </button>
        </div>
      </div>
      <div class='ui bottom attached green basic button' v-if="todo.done">
        All done!
      </div>
      <div class='ui bottom attached red basic button' v-else v-on:click="completeTodo(todo)">
        Finish todo.
      </div>
    </div>
    
    <!-- form is visible when we are in editing mode -->
    <div class="ui centered card" v-else>
      <div class="content">
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input type='text' v-model="todo.title" >
          </div>
          <div class='field'>
            <label>Project</label>
            <input type='text' v-model="todo.project" >
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="hideEditForm">
              <i class="save icon"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data() {
      return {
        isNotEditMode: true
      };
    },
    methods: {
      showEditForm() {
        this.isNotEditMode = false;
      },
      hideEditForm() {
        this.isNotEditMode = true;
      },
      deleteForm(todo) {
        this.$emit('delete-todo', todo);
      },
      completeTodo(todo) {
        this.$emit('completed-todo', todo)
      }
    },
  };
</script>

<style scoped>

</style>