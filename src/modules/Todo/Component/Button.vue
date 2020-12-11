<template>
<div>
    <div v-if="!role">
        <button  v-on:click="deleteTask">{{name}}</button>
    </div>
    <div v-if="role">
        <button  v-on:click="editTask">{{name}}</button>
    </div>
</div>
</template>

<script>
export default {
    name: 'Button',
    inject: [
        'delete'
    ],
    props: {
        name: String,
        task: Object,
        role: String,
    },
    methods: {
        deleteTask() {
            this.delete(this.task)
        },
        editTask() {
            this.$emit('edit', this.task)
        }
    },
    created() {
        console.log(this.task);
    }

}
</script>

<style>

</style>