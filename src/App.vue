<template>
  <div id="app">
    <h1>{{ formTitle }}</h1>
    <br>
    Add todo:
    <input v-model="newTodo" placeholder='Enter a task'/>
    <br>
    <button v-on:click='onSubmit(newTodo)'>Submit</button>
    <br>
    <ol>
      <li v-for='todo in todos' :key='todo.id' class='todos'>
      {{ todo.title }}
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      formTitle: 'Form: ',
      newTodo: '',
      todos: [],
      todoCount: 0
    }
  },
  methods: {
    onSubmit: function (newTodo) {
      this.todoCount++;
      this.todos.push({
        title: this.newTodo,
        id: this.todoCount
      });
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
