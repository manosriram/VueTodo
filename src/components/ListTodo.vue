<template>
    <div class="todo">
        <u><h3>Your Todos</h3></u>
        <div v-bind:key="todo" v-for="todo in todos">
            <h3>{{ todo }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    name: "ListTodo",
    props: {
        todos: Array
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
