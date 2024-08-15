<template>
    <div class="main-app">
        <h1>Todo App</h1>
        <div class="todo-app">
            <div class="task-input">
                <input type="text" placeholder="Add new todo" @keyup.enter="addTask" v-model="newTask">
                <button @click="addTask">Add todo</button>
            </div>
            <ul class="task-list">
                <li v-for="(task, index ) in tasks" :key="index" class="task-item">
                    {{ task }}
                    <button @click="removeTask(index)" class="remove-button">Remove todo</button>
                </li>
    
            </ul>
    
        </div>
    </div>
    
</template>

<script>
import {ref} from 'vue'
    export default {
        name: 'TodoList',
        setup() {
            const newTask = ref('');
            const tasks = ref([ ]);

            const addTask = () => {
                if (newTask.value.trim() !== '' ) {
                    tasks.value.push(newTask.value)
                    newTask.value = ' '
                }

            }

            const removeTask = (index) => {
                tasks.value.splice(index, 1)

            }
            return {
                addTask,
                removeTask,
                tasks,
                newTask
            }

            
        }
    }
</script>

<style scoped>
.main-app {
    max-width: 600px;
    border: 1px solid #ccc;
    border-radius: 8px;
    margin: 50px auto;
    padding: 20px;
    background-image:linear-gradient(#403020, #ffd3ea);
}
h1{
    text-align: center;
    font-style: italic;
    color: #ddd;
}

.todo-app {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .app-title {
    font-size: 24px;
    margin-bottom: 20px;
    text-align: center;
    color: #333;
  }
  
  .task-input {
    display: flex;
    gap: 10px;
  }
  
  input {
    flex: 1;
    padding: 8px;
    font-size: 14px;
  }
  
  button {
    padding: 8px 12px;
    font-size: 14px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #45a049;
  }
  
  .task-list {
    list-style: none;
    padding: 0;
  }
  
  .task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px 0;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  .remove-button {
    padding: 6px 10px;
    font-size: 12px;
    background-color: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  
  .remove-button:hover {
    background-color: #c0392b;
  }
  .header {
    text-decoration: green;
  }



</style>