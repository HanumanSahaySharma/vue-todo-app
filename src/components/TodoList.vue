<template>
  <div class="todo-body">
    <div class="todo-list" v-if="todos.length > 0">
        <div class="todo-item d-flex align-items-center justify-content-between" v-for="(todo, index) in todos" :key="index">
            <div class="todo-item-heading d-flex align-items-center">
                <div class="custom-checkbox">
                    <input type="checkbox" :value="todo.title" v-model="todo.selected" @change="$emit('selectTodo', todo)" />
                    <span class="custom-checkbox-area"></span>
                </div>
                <h2>{{ todo.title }}</h2>
            </div>
            <button class="btn btn-danger btn-sm" @click="$emit('removeSingleTodo', index)">Remove</button>
        </div>
    </div>
    <div class="text-center" v-else>
      <h5 class="mt-15 mb-15 smiley-icon">&#128526;</h5>
      <p class="mb-0">Hurray! there are no pending item.</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ['todos', 'selectedTodosLength'],
  methods: {
    selectAllTodos () {
      this.todos.filter((todo) => {
        if (todo) {
          todo.selected = true
        }
      })
    }
  }
}
</script>
