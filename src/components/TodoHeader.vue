<template>
    <div class="todo-header d-flex align-items-center justify-content-between">
        <div class="heading">
            <h1>Todos</h1>
            <p class="todo-count">{{ todoCount }}</p>
        </div>
        <button class="btn btn-primary-inverse" @click="$emit('toggleTodoForm')">
          {{ !toggleForm ? 'Add Todo' : 'Hide Form'}}
        </button>
    </div>
</template>
<script>
export default {
  props: ['todoCount', 'toggleForm']
}
</script>
