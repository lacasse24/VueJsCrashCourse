
<template>
    <div>
        <div v-bind:key="todo.id"  v-for="todo in todosProps">
           <TodoItem v-bind:todoProps="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todosProps"]
}
</script>

<style scoped>

</style>