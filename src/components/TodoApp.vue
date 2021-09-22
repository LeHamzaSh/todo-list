<template>
  <div class="container">
    <h2 class="text-center mt-5">Hamza's Todo List</h2>

    <!-- Input -->
    <div class="d-flex">
      <input type="text" placeholder="Enter Task" class="form-control">
      <button class="btn btn-danger rounded-0">Submit</button>
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
    <tr>
      <td>Play pingpong</td>
      <td>To-do</td>
      <td></td>
      <td></td>
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
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
