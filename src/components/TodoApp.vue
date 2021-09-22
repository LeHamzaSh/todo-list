<template>
  <div class="container">
    <h2 class="text-center mt-5">Hamza's Todo List</h2>

    <!-- Input -->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter Task" class="form-control">
      <button @click="submitTasks" class="btn btn-danger rounded-0">Submit</button>
    </div>

    <!-- Table for Tasks -->

    <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" :key="index">
      <!-- Display the name of the Task -->
      <td>{{ task.name }}</td>

      <!-- Display the status of the Task -->
      <td>{{ task.status }}</td>

      <td>
        <div class="text-center">
          <span class="fa fa-pen"></span>
        </div>
      </td>

      <td>
        <div class="text-center">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data(){
    return{
      task: '',
      tasks:[
        {
          name: 'Play Ping Pong.',
          status: 'to-do'
        },
        {
          name: 'Take out Trash',
          status: 'in-progress'
        }
      ] 
    }
  },

  methods:{
    submitTasks(){
      if(this.task.length === 0){
        return alert('It cannot be empty!!')
      }
      this.tasks.push({
        name: this.task,
        status: 'to-do'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
