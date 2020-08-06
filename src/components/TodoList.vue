<template>
  <div class="container">
    <h1>
      VueJs TodoList ({{
        todos.filter((t) => !t.done).length
      }})
    </h1>
    <div class="todo-creator">
      <input
        class="input"
        type="text"
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="New Task"
      />
      <button
        class="btn"
        @click="addTask"
      >
        Add Task
      </button>
    </div>
    <div
      class="todo-item"
      v-bind:class="{ 'todo-item--completed': todo.done }"
      v-for="todo in todos"
      :key="todo.id"
      @click="completeTask(todo)"
    >
      {{ todo.title }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      newTask: '',
      todos: [
        { id: 1, title: 'learn vuejs', done: false},
        { id: 2, title: 'learn reactjs', done: false},
        { id: 3, title: 'learn angularjs', done: false},
      ]
    };
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.todos.push({
          title: this.newTask,
          done: false,
        });
        this.newTask = ''
      }
    },
    completeTask(task) {
      task.done = !task.done;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  .todo-item {
    border-radius: 5px;
    padding: 10px 20px;
    margin: 5px;
    width: 80%;
    background-color: blue;
    color: white;
    font-weight: 600;
  }

  .todo-item--completed {
    text-decoration: line-through;
  }

  .todo-creator {
    display: flex;
    width: 100%;
    justify-content: center;
    margin-bottom: 50px;
  }

  .input {
    font-size: 20px;
    background: lightblue;
    border-color: blue;
    border-radius: 5px;
    color: darkred;
    padding: 5px 20px;
    margin-right: 20px;
  }

  .btn {
    background-color: green;
    padding: 10px 5px;
    border: none;
    font-size: 20px;
    border-radius: 5px;
    color: white;
  }
</style>
