<template>
    <div class="container">
        <h1 class="title">To-Do</h1>
        <form class="form">
            <input type="text" name="input" id="input" v-model="input" placeholder="Input new to-do">
            <button type="button" @click="addToDo">Add</button>
        </form>

        <ul class="list">
            <li v-for="(item, index) in todos" :key="index">
                {{ item.title }} <button class="btn btn-danger" @click="deleteToDo">Delete</button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data: function(){
            return{
                todos: [],
                input: null,
            }
        },
        methods: {
            addToDo(){
                const newToDo = {
                    title: this.input
                }
                this.input = null
                this.todos = [...this.todos, newToDo]
            },
            deleteToDo(index){
                this.todos.splice(index, 1)
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
