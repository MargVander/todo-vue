<template>
  <div>
    <h1>Todo list</h1>
    <Display :tasks='tasks' />
    <Add @addTodo='addTodo'  />
  </div>
</template>

<script>
import Add from './Component/Add'
import Display from './Layout/Display'
export default {
  name: 'Todo',
  components: {
    Add,
    Display
  },
  data : () => {
    return {
      tasks: [],
    }
  },
  methods: {
    addTodo(name) {
      this.tasks.push({
        id: Date.now(),
        name: name,
        state: false,
      })
    },
    deleteTodo(task) {
      console.log(task.id)
       this.tasks = this.tasks.filter((t) => t.id !== task.id);
    }
  },
  provide() {
    return {
      delete: this.deleteTodo,
    };
  }
}
</script>

<style>

</style>
