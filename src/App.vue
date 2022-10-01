<template>
  <div>
    <div class="container mt-5 card">
      <div class="row mt-4">
        <div class="col-md-10">
          <h2>Todo App Vue Composition API</h2>
        </div>

        <div class="row mt-3">
          <div class="col-md-10">
            <input type="text" class="form-control" v-model="todo" @keyup.enter="addTodo">
          </div>
          <div class="col-md-2">
            <button class="btn btn-info" @click="addTodo">Add</button>
          </div>

          <TodoComponent :todos="todos" @doneTodo="doneTodo" @deleteTodo="deleteTodo"/>

        </div>

        <small class="my-4 text-center">todo : {{ totalTodos }} </small>

      </div>
    </div>
  </div>
</template>


<script>
import {ref, reactive, computed, onMounted} from 'vue'

import TodoComponent from './components/todo/component_todo.vue'

export default {
  components: { TodoComponent },

  setup() {
    const todo = ref('')

    const todos = reactive({
      list: []
    })



    const addTodo = () => {
      todos.list.unshift({
        activity: todo.value,
        isDone: false
      })

      todo.value = ''
      saveToStorage()
    }

    const doneTodo = (index) => {
      todos.list[index].isDone = !todos.list[index].isDone
      saveToStorage()
    }

    const deleteTodo = (index) => {
      todos.list = todos.list.filter((todo) => todos.list.indexOf(todo) != index)
      saveToStorage()
    }

    const saveToStorage = () => {
      localStorage.setItem('todos', JSON.stringify(todos))
    }

    onMounted(() => {

      if (todos.list != []) {
        todos.list = JSON.parse(localStorage.getItem('todos')).list
      } else {
        saveToStorage()
      }
      
    })

    const totalTodos = computed(() => {
      return todos.list.length
    })

    return {
      todo, todos, addTodo, totalTodos, doneTodo, deleteTodo
    }
  },
  
}
</script>