<template>
  <div>
    <ul>
      <h2>Finalizados</h2>
      <li v-for="todo in $doneTodos" :key="todo.id">
        {{ todo.text }}
      </li>
    </ul>

    <ul>
      <h2>Não finalizados</h2>
      <li v-for="todo in $currentTodos" :key="todo.id">
        {{ todo.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    $doneTodos() {
      return this.$store.getters.$doneTodos
    },
    $currentTodos() {
      return this.$store.getters.$currentTodos
    }
  },
  created() {
    this.$store.dispatch("fetchTodos")
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
