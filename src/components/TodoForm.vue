<template>
  <div class="todo-form">
      <form @submit.prevent="submitTodo">
        <div class="form-group">
            <input type="text" v-model="todoName" placeholder="Enter Todo Name Here" />
        </div>
        <p class="alert alert-danger mb-0" v-if="isError && checkError">Please enter your todo first.</p>
      </form>
  </div>
</template>
<script>
export default {
  data () {
    return {
      todoName: '',
      isError: false
    }
  },
  computed: {
    checkError () {
      return this.todoName.length <= 0
    }
  },
  methods: {
    submitTodo () {
      if (this.todoName.length > 0) {
        this.isError = false
        this.$emit('submitTodo', this.todoName)
        this.todoName = ''
      } else {
        this.isError = true
      }
    }
  }
}
</script>
