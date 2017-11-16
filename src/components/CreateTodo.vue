<template>
  <section>
    <div class='ui basic content center aligned segment'>
      <div class='ui centered card' v-if="isCreating">
        <div class='content'>
          <div class='ui form'>
            <div class='field'>
              <label>Title</label>
              <input v-model="todoTitle" type='text' ref='title' defaultValue="">
            </div>
            <div class='field'>
              <label>Project</label>
              <input type='text' v-model="todoProject"  ref='project' defaultValue="">
            </div>
            <div class='ui two button attached buttons'>
              <button class='ui basic blue button' v-on:click="addTodo">
                Create
              </button>
              <button class='ui basic red button' v-on:click="closeForm">
                Cancel
              </button>
            </div>
          </div>
        </div>
      </div>
      
      <button class="ui labeled icon button" v-on:click="openForm" v-else>
        <i class="add icon"></i>
        Add new todo
      </button>
    </div>
  </section>
</template>

<script type='text/javascript'>
  export default {
    data() {
      return {
        isCreating: false,
        todoTitle: '',
        todoProject: ''
      }
    },
    methods: {
      openForm () {
        this.isCreating = true;
      },
      closeForm () {
        this.isCreating = false;
      },
      addTodo() {
        let title = (this.todoTitle).trim(),
            project = (this.todoProject).trim();
            
        console.log(title + ' ' + project)
        if (title != '' && project != '') {
          this.$emit('create-todo', {
            title,
            project,
            done: false
          })
        }
        
        this.isCreating = false;
      }
    }
  }
</script>