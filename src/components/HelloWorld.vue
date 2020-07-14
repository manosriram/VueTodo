<template>
    <div class="hello">
        <h1>Vue Todo!</h1>
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
        <br />
        <br />
        <button @click="fetchApi()">Fetch API</button>

        <div v-if="this.fetchedData">
            <br />
            <h2>
                <strong>{{ this.fetchedData }}</strong>
            </h2>
            <hr />
        </div>
        <div v-else>
            <br />
            Not yet clicked!
        </div>

        <div v-if="this.todos.length">
            <ListTodo v-bind:todos="this.todos" />
        </div>
        <div v-else>
            <h3>Todo List Empty!</h3>
        </div>
    </div>
</template>

<script>
import ListTodo from "./ListTodo.vue";
const api = "https://jsonplaceholder.typicode.com/todos";

export default {
    name: "HelloWorld",
    components: {
        ListTodo
    },
    data() {
        return {
            todos: [],
            currentTodo: "",
            fetchedData: null
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
            if (this.currentTodo.length === 0) return;
            this.todos.push(this.currentTodo);
            this.currentTodo = "";
        },
        async fetchApi() {
            const number = Math.floor(Math.random() * 101);
            const data = await fetch(`${api}/${number}`);
            const json = await data.json();
            this.fetchedData = json;
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
input {
    width: 50%;
    height: 30px;
    text-align: center;
    outline: none;
}
input::placeholder {
    color: black;
}
button {
    background: black;
    border-color: black;
    color: white;
    width: 10%;
    height: 30px;
    border-radius: 5px;
    outline: none;
}
button:hover {
    cursor: pointer;
}
</style>
