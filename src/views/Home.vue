<template>
    <div>
       
        <AddTask v-if="showAddTask" @add-task= "addTask" />
        <Tasks @delete-task= "deleteTask" :tasks="tasks" @toggle-reminder= "toggleReminder" />
    </div>
</template>

<script>
import Tasks from "../components/Tasks"
import AddTask from '../components/AddTask'
export default {
    name:'Home',
    props:{
        showAddTask: Boolean
    },
    components: {
        Tasks,
        AddTask
    },
    data () {
        return{
            tasks : []
        }
    },

    methods: {
    async deleteTask(id) {
      const res = await fetch(`api/tasks/${id}`,{
        method:'DELETE'
      })

      res.status === 200 ? (this.tasks = this.tasks.filter((task) => task.id !== id)) : alert('error deleting task')
      
    },
    
    async toggleReminder (id){
      const tasktoToggle = await this.fetchTask(id)
      const updTask = {...tasktoToggle, reminder: !tasktoToggle.reminder}

      const res = await fetch(`api/tasks/${id}`, {
        method:'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updTask)
      })
      const data = await res.json()
      this.tasks = this.tasks.map((task) => task.id === id ?  {...task, reminder: data.reminder } : task)
    },

    async addTask(newTask){
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers:{
          'Content-type': 'Application/json'
        },
        body: JSON.stringify(newTask)
      })

      const data = await res.json()
      this.tasks = [...this.tasks, data]
    },

    async fetchTasks () {
      const response = await fetch("api/tasks")
      const data = await response.json()
      return data
    },

    async fetchTask (id) {
      const response = await fetch(`api/tasks/${id}`)
      const data = await response.json()
      return data
    }
  },

  async created() {
    this.tasks = await this.fetchTasks()
  }
}

</script>

<style scoped>

</style>