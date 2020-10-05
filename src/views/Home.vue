<template>
<div>
  <AddTodo @add-todo="AddTodo"/>
  <table id="todo" :newID="[todos.length + 1]">
  <tr v-for="todo in todos" :key="todo.id">
    <Todo :todo="todo" @delete-task="deleteTodo"/>
  </tr>
</table>
</div>
</template>

<script>
import Todo from './todo.vue';
import AddTodo from './AddTodo.vue';

export default {
  name: 'Home',
  data() {
    return {
      todos: [
        { id: 1, task: 'clean the toilet', completed: false },
        { id: 2, task: 'buy groceries', completed: false },
        { id: 3, task: 'go to school', completed: true },
      ],
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
