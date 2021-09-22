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
      <td><span :class="{'completedItem': task.status === 'Completed'}">{{ task.name }}</span></td>

      <!-- Display the status of the Task -->
      <!-- The Statuses are clickable to change -->
      <td style="width: 140px"><span @click="statusChange(index)" class="pointer" 
      :class="{'text-danger': task.status === 'To-do',
      'text-warning': task.status === 'In-progress',
      'text-success': task.status === 'Completed'}">
        {{ task.status }}
        </span></td>

      <td>
        <div class="text-center" @click="editItem(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>

      <td>
        <div class="text-center" @click="deleteItem(index)">
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
      editedItem: null,
      //update statuses array
      statusAvailabile: ['To-do', 'In-progress', 'Completed'],

      //Store items in the task array
      tasks:[] 
    }
  },

  methods:{
    submitTasks(){
      if(this.task.length === 0){
        return alert('It cannot be empty!!')
      }
      if(this.editedItem === null){
      this.tasks.push({
        name: this.task,
        status: 'To-do'
      })
      }

      else{
        this.tasks[this.editedItem].name = this.task;
        this.editedItem = null;
      }

      // Reset the Enter Task after entering data
      this.task = '';
    },

    deleteItem(index){
      /* Remove the Item from the array */
      this.tasks.splice(index, 1) // Remove only 1 item
    },

    editItem(index){
      this.task = this.tasks[index].name
      this.editedItem = index

    },

    statusChange(index){
      //Loop over the statuses on each click
      let indexTwo  =this.statusAvailabile.indexOf(this.tasks[index].status);
      if(++indexTwo > 2) indexTwo = 0
      this.tasks[index].status = this.statusAvailabile[indexTwo]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pointer{
  cursor: pointer;
}

.completedItem {
  text-decoration: line-through;

}
</style>
