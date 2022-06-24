<template>
    <div class="todo-header d-flex align-items-center justify-content-between">
        <div class="heading">
            <h1>Todos</h1>
            <p class="todo-count">{{ todoCount }}</p>
        </div>
        <appButton :title="!toggleForm ? 'Add Todo' : 'Hide Form'" varient="primary-inverse" v-on:onClick="$emit('toggleTodoForm')"></appButton>
    </div>
</template>
<script>
import appButton from '@/components/Button/index'
export default {
  name: 'todo-header',
  props: ['todoCount', 'toggleForm'],
  components: {
    appButton
  }
}
</script>
