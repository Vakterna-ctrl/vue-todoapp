<template>
    <div>
    <input type="text" v-model="title"/>
    <button @click="addTodo">Add Todo</button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    };
  },
  props: {
    newID: Number,
  },
  methods: {
    addTodo() {
      axios.post('https://jsonplaceholder.typicode.com/users/1/todos',
        {
          title: this.title,
          completed: false,
        }).then((res) => {
        this.$emit('add-todo', res.data);
        this.title = '';
      });
    },
  },

};
</script>

<style scoped>
div {
    width: 500px;
    display: flex;
}
input {
    width: 400px;
}
button {
    width: 100px;
}

</style>
