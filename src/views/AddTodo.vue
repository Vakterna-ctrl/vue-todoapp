<template>
    <div>
    <input type="text" v-model="title"/>
    <button @click="addTodo">Add Todo</button>
    </div>
</template>

<script>
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
      const newTodo = {
        id: this.newID,
        title: this.title,
        completed: false,
      };
      this.$emit('add-todo', newTodo);
      this.title = '';
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
