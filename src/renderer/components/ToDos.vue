<template>
    <div>
        <div>
            <div>
                <button @click="fetchTodos()" class="btn btn-primary">Fetch Todos</button>
            </div>
        </div>
        <div>
            <div>
                <ul>
                    <li v-for="todo in todos" :key="todo.id"></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
  const axios = require('axios')
  export default {
    name: 'ToDos',
    data: () => {
      return {
        todos: []
      }
    },
    methods: {
      async fetchTodos () {
        axios
          .get('http://localhost:3001/')
          .then(response => {
            this.todos = response.data
          })
          .catch(error => {
            if (error) throw new Error(error)
          })
      }
    }
  }
</script>

<style scoped>

</style>
