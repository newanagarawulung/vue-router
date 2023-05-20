<template>
  <div class="todo-list">
    <h1 class="todo-list__title">To-Do List</h1>
    <ul class="todo-list__tasks">
      <li v-for="(task, index) in tasks" :key="index" class="todo-list__task">
        <label class="todo-list__task-label">
          <input type="checkbox" v-model="task.completed" class="todo-list__task-checkbox">
          <span class="todo-list__task-name">{{ task.name }}</span>
        </label>
        <div class="todo-list__task-actions">
          <button @click="editTask(index)" class="todo-list__task-action">Edit</button>
          <button @click="deleteTask(index)" class="todo-list__task-action">Delete</button>
        </div>
      </li>
    </ul>
    <form @submit.prevent="addTask" class="todo-list__add-form">
      <input type="text" v-model="newTaskName" class="todo-list__add-input" placeholder="Enter task name">
      <button class="todo-list__add-button">Add Task</button>
    </form>
    <p class="todo-list__incomplete-tasks">{{ incompleteTasks }} tasks remaining</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tasks: [
        { name: 'Task 1', completed: false },
        { name: 'Task 2', completed: true },
        { name: 'Task 3', completed: false }
      ],
      newTaskName: ''
    }
  },
  computed: {
    incompleteTasks() {
      return this.tasks.filter(task => !task.completed).length
    }
  },
  methods: {
    addTask() {
      if (this.newTaskName.trim() !== '') {
        this.tasks.push({
          name: this.newTaskName.trim(),
          completed: false
        })
        this.newTaskName = ''
      }
    },
    editTask(index) {
      const newName = prompt('Enter new task name:', this.tasks[index].name)
      if (newName !== null && newName.trim() !== '') {
        this.tasks[index].name = newName.trim()
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
<style>

.todo-list {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  background-color: transparent;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.todo-list__title {
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 20px;
  color: white;
}

.todo-list__tasks {
  list-style: none;
  margin: 0;
  padding: 0;
}

.todo-list__task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.todo-list__task-label {
  display: flex;
  align-items: center;
}

.todo-list__task-checkbox {
  margin-right: 10px;
}

.todo-list__task-actions {
  display: flex;
}

.todo-list__task-action {
  margin-right: 10px;
  font-size: 14px;
  padding: 5px 10px;
  border-radius: 4px;
  border: none;
  background-color: #2fb056;
  color: rgb(0, 0, 0);
}

.todo-list__add-form {
display: flex;
margin-top: 20px;
}

.todo-list__add-input {
flex-grow: 1;
padding: 10px;
font-size: 16px;
border-radius: 4px;
border: none;
background-color: #eee;
color: rgb(6, 2, 2);
}

.todo-list__add-button {
margin-left: 10px;
font-size: 16px;
padding: 10px 20px;
border-radius: 4px;
border: none;
background-color: #2fb056;
color: white;
cursor: pointer;
}

.todo-list__incomplete-tasks {
margin-top: 20px;
font-size: 16px;
font-style: italic;
color: white;
}
</style>
