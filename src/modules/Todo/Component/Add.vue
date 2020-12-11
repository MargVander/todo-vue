<template>
  <input type="text" v-model="task" @keydown.enter="add" />
</template>

<script>
export default {
    name: 'Add',
    data: () => {
        return {
            task: '',
        }
    },
    methods: {
        add() {
            if (this.task !== '') {
                this.$emit('addTodo', this.task)
                this.task = ''
            }
        }
    }
}
</script>

<style>

</style>