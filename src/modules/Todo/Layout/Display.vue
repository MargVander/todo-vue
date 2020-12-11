<template>
<ul>
    <li v-for='task in tasks' :key="task.id">
        <div v-if="taskToEdit === task">
            <input v-model="task.name" @keydown.enter="validateTask" />
        </div>
        <div v-else>
            {{task.name}}
             <Button name="X" :task="task" />
             <Button name="modifier" :task="task" role="edit" @edit="editTask" />
        </div>
    </li>
</ul>
  
</template>

<script>
import Button from '../Component/Button'
export default {
    components: {
        Button,
    },
    name: 'Display',
    props: {
        tasks: Array,
    },
    data: () => {
        return {
            taskToEdit: null,
        }
    },
    methods: {
        editTask(task) {
            this.taskToEdit = task
        },
        validateTask() {
            console.log("validate");
            
            this.taskToEdit = null;
            
        }
    }
}
</script>

<style>
ul{
    list-style-type: none;
}
</style>