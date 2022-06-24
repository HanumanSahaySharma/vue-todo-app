<template>
  <div class="todo-app-container">
      <TodoHeader v-on:toggleTodoForm="toggleTodoForm" :todoCount="todoCount" :toggleForm="toggleForm"/>
      <TodoForm v-if="toggleForm" v-on:submitTodo="submitTodo($event)" />
      <TodoList
          :todos="todos"
          v-on:removeSingleTodo="removeSingleTodo($event)"
          v-on:selectTodo="selectTodo($event)"
          v-on:selectAllTodos="selectAllTodos"
        />
        <div class="btn-group d-flex align-items-center justify-center-center mb-15" v-if="todos.length > 0">
          <appButton title="Deselect All Todos" v-if="selectedTodos.length > 0" varient="primary" size="sm" v-on:onClick="deselectAllTodos"></appButton>
          <appButton title="Select All Todos" v-if="!selectedTodos.length > 0" varient="primary" size="sm" v-on:onClick="selectAllTodos"></appButton>
          <appButton :disabled="disableRemoveSeletedTodosBtn" title="Remove Selected Todos" varient="danger" size="sm" v-on:onClick="removeAllSelectedTodos"></appButton>
        </div>
  </div>
</template>

<script>
import TodoHeader from '@/components/TodoHeader'
import TodoForm from '@/components/TodoForm'
import TodoList from '@/components/TodoList'
import appButton from '@/components/Button/index'
export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoForm,
    TodoList,
    appButton
  },
  data () {
    return {
      title: 'Hello World!',
      todos: [
        { title: 'Go to Gym at 7 AM', selected: false },
        { title: 'Make a video for YouTube', selected: false },
        { title: 'Read the Newspaper everyday', selected: false }
      ],
      selectedTodos: [],
      toggleForm: false,
      isEnabled: false
    }
  },
  computed: {
    todoCount () {
      return this.todos.length
    },
    disableRemoveSeletedTodosBtn () {
      return this.selectedTodos.length <= 0
    }
  },
  mounted () {
    this.checkCoding()
  },
  methods: {
    checkCoding () {

    },
    toggleTodoForm () {
      this.toggleForm = !this.toggleForm
    },
    submitTodo (todo) {
      this.todos.push({
        title: todo,
        selected: false
      })
    },
    removeSingleTodo (todo) {
      this.todos.splice(todo, 1)
      this.selectedTodos.filter((singleTodo) => {
        if (singleTodo.selected === true) {
          this.selectedTodos.splice(singleTodo, 1)
        }
      })
    },
    selectTodo (todo) {
      if (todo.selected === true) {
        this.selectedTodos.push(todo)
      } else if (todo.selected === false) {
        this.selectedTodos.splice(todo, 1)
      }
    },
    removeAllSelectedTodos (removeTodo) {
      const newArray = this.todos.filter((todoItem) => {
        return !this.selectedTodos.includes(todoItem)
      })
      this.selectedTodos.splice(removeTodo, 1)
      this.todos = newArray
      this.selectedTodos = []
    },
    selectAllTodos () {
      this.todos.filter((todoItem) => {
        todoItem.selected = !todoItem.selected
        this.selectTodo(todoItem)
        if (todoItem.selected === false) {
          todoItem.selected = true
          this.selectTodo(todoItem)
        }
      })
    },
    deselectAllTodos () {
      this.selectedTodos = []
      this.todos.filter((todoItem) => {
        todoItem.selected = false
      })
    }
  }
}
</script>
