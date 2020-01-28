<template>
    <div class = "todo-item" v-bind:class="{'is-complete':todoProps.completed}">
       <p>
           <input type = "checkbox" v-on:change="markCompleted"> 
           {{todoProps.title}}
           <button @click="$emit('del-todo',todoProps.id)" class="del">X</button>
       </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todoProps"],
    methods: {
        markCompleted() {
            this.todoProps.completed = !this.todoProps.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: lightgrey;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: red;
        color: white;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>