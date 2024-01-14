<template>
  <div class="container">
    <div class="flex-col">
      <div class="sub-container">
        <input type="text" v-model="newTodo" @keyup.enter="addTodo" />
        <button @click="addTodo">Add Todo</button>
      </div>
      <div class="sub-container">
        <ul>
          <li v-for="todo in todos" :key="todo.id">
            {{ todo.text }}
            <button @click="deleteTodo(todo.id)">Delete</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo,
        });
        this.newTodo = "";
      }
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style scoped>
.flex-col {
  display: flex;
  flex-direction: column;
}
.container {
  max-width: 400px;
  margin: 2rem auto;
  padding: 1rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  background-color: #f9f9f9;
  display: flex;
}

.sub-container {
  display: flex;
  color: #0056b3;
}

input[type="text"] {
  width: 70%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-right: 1rem;
}

button {
  padding: 0.5rem 1rem;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-top: 1rem;
  background-color: #fff;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li button {
  padding: 0.3rem 0.6rem;
  background-color: #dc3545;
}

li button:hover {
  background-color: #c82333;
}
</style>
