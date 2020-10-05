<template>
    <td :class="{'completed':todo.completed}">
      <input type="checkbox" @click="markComplete" :checked="todo.completed"/>{{ todo.title }}
      <button class="del" @click="deleteTask">X</button>
      </td>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    todo: Object,
  },
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
      console.log(!this.todo.completed);
    },
    deleteTask() {
      this.$emit('delete-task', this.todo.id);
      console.log(this.todo.id);
    },

  },
};
</script>

<style scoped>
td {
  border: 1px solid #ddd;
  padding: 8px;
  font-size: 18px;
  text-align: center;
  position: relative;
}
input {
  position: absolute;
  left: 5px;
}
.completed {
    text-decoration: line-through;
}
.del {
  position: absolute;
  right: 5px;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  color: white;
  background-color: red;
  padding: 0px;

}

</style>
