<template>
  <section id="todoapp">
    <header class="header">
      <h1>Tarefas</h1>
      <input-task @newTask='addTask'></input-task>
      <task-list  :todo-list='tasks'></task-list>
    </header>
  </section>
</template>

<script>
import InputTask from './components/InputTask'
import TaskList  from './components/TaskList'
import { Task }  from './models/Task'

// tasks.push(task)
// tasks.push(task)
// tasks.push(task)

export default {
  name: 'App',
  components: {
   InputTask,
   TaskList
  },
  data () {
    return {
     tasks: []
    }
  },
  methods: {
    addTask (task) {
     this.tasks.push(task)
     console.log('Task added')
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
