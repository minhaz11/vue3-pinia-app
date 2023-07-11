<template lang="">
    <form @submit.prevent="handleSubmit">
        <input type="text" v-model="task" placeholder="Add a task" />
        <button type="submit">Add</button>
    </form>
</template>

<script setup>
    import { ref } from 'vue'
    import { useTaskStore } from '../stores/TaskStore.js'

    const taskStore = useTaskStore()
    const task = ref('')

    function handleSubmit() {
        if(task.value.length > 0){
            taskStore.addTask({
                title: task.value,
                isFav : false,
                id: Math.floor(Math.random() * 1000)
            })
        }
        task.value = ''
    }

</script>
