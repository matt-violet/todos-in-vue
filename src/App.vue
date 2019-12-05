<template>
  <div id="app">
    <h1>{{ formTitle }}</h1>
    <br>
    Add a task:
    <input v-model="newTodo" id='input' placeholder='new task'/>
    <br>
    <button v-on:click='onSubmit(newTodo)'>Submit</button>
    <br>
    <ol>
      <li v-for='todo in todos' :key='todo.id' class='todos'>
      {{ todo }} <button v-on:click='onDelete(todo)'>delete</button>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      formTitle: 'To-Do List: ',
      newTodo: '',
      todos: [],
    }
  },
  methods: {
    onSubmit: function (newTodo) {
      this.todos.push(this.newTodo);
      this.newTodo = '';
    },
    onDelete: function (todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

.todos {
  text-align: left;
}

a {
  color: #42b983;
}
</style>
