<template>
  <div class="container">
    <div class="todo-card">
      <h1 class="text-center mt-5">Vue Todo App</h1>
      <div class="w-50 mx-auto">
        <!-- Input,s -->
        <input type="text" placeholder="Enter a task" class="form-control mb-4">
        <input type="text" placeholder="Description" class="input-lg form-control mb-4">
        <div class="text-center">
          <button class="btn btn-primary btn-lg">Submit</button>
        </div>
      </div>
    </div>

    <!-- Tasks Table -->
    <div class="todo-card">
      <table class="table table-bordered">
        <thead>
          <tr>
            <th scope="col">Task</th>
            <th scope="col">Description</th>
            <th scope="col">Edit</th>
            <th scope="col">Trash</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Steal bnana,s from store</td>
            <td>To-do</td>
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
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    msg: String
  },

  data() {
    return {
      tasks: [
        {
          name: 'Banana,s',
          description: 'Steal banana,s from store'
        },
        {
          name: 'Choclate',
          description: 'Eat 1kg choclate after meal'
        }
      ]
    }
  }
}
</script>

<style scoped>
  .todo-card{
    margin: 25px auto;
    border-radius: 6px;
    background-color: #FFFFFF;
    box-shadow: 0 0 14px 0 rgb(0 0 0 / 7%);
  }
</style>
