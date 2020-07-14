<template>
    <div class="hello">
        <input
            id=""
            type="text"
            placeholder="Todo here"
            :value="this.currentTodo"
            v-on:change="updateTodo($event)"
        />
        <br />
        <br />
        <button @click="addTodo()">Add Todo</button>

        <ListTodo v-bind:todos="this.todos" />
    </div>
</template>

<script>
import ListTodo from "./ListTodo.vue";
export default {
    name: "HelloWorld",
    components: {
        ListTodo
    },
    data() {
        return {
            todos: [],
            currentTodo: ""
        };
    },
    props: {
        msg: String
    },
    methods: {
        updateTodo(e) {
            this.currentTodo = e.target.value;
        },
        addTodo() {
            this.todos.push(this.currentTodo);
            this.currentTodo = "";
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
