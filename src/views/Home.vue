<template>
<div>
  <AddTodo @add-todo="AddTodo"/>
  <table id="todo" :newID="[todos.length + 1]">
  <tr v-for="todo in todos" :key="todo.title ">
    <Todo :todo="todo" @delete-task="deleteTodo"/>
  </tr>
</table>
</div>
</template>

<script>
import axios from 'axios';
import Todo from './todo.vue';
import AddTodo from './AddTodo.vue';

export default {
  name: 'Home',
  data() {
    return {
      todos: [],
    };
  },
  components: {
    Todo,
    AddTodo,
  },
  methods: {
    deleteTodo(id) {
      console.log(id);
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    test() {
      console.log('yikes');
    },
    AddTodo(newtodo) {
      this.todos = [...this.todos, newtodo];
    },
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/users/1/todos')
      .then((res) => { this.todos = res.data; });
  },
};
</script>
 <style lang="scss" scoped>
 #todo {
  font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 500px;
  border: 1px solid black
}

#todo tr:nth-child(even){background-color: #f2f2f2;}

#todo tr:hover {background-color: #ddd;}

 </style>
