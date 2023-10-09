<template>
  <h2>Todo Count: {{ todoCount }}</h2>
  <ul>
    <li v-for="{ todo } in todos" :key="todo">{{ todo }} <button @click="removeTodo(todo)">X</button></li>
  </ul>
  <input type="text" v-model.trim="newTodo">
  <button @click="addTodo">Add Todo</button>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "Forth Task",
      todos: [
        { todo: "First task" },
        { todo: "Second task" },
        { todo: "Third task" },
      ],
    };
  },
  methods: {
    addTodo () {
      if (this.newTodo !== '') {
        this.todos.push({ todo: this.newTodo });
        this.newTodo = ''
      }
    },
    removeTodo (todo) {
      this.todos = this.todos.filter(e => e.todo != todo);
    }
  },
  computed: {
    todoCount() {
      return this.todos.length;
    }
  }
};
</script>
