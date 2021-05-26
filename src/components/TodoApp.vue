<template>
  <div class="container">
    <div class="todo-card">
      <h1 class="text-center mt-5">Vue Todo App</h1>
      <div class="w-50 mx-auto">
        <!-- Input,s -->
        <input v-model="task" type="text" placeholder="Enter a task" class="form-control mb-4">
        <input v-model="description" type="text" placeholder="Description" class="input-lg form-control mb-4">
        <div class="text-center">
          <button @click="submitTask()" class="btn btn-primary btn-lg">Submit</button>
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
          <tr v-for="(task, index) in tasks" :key="index">
            <td>{{task.name}}</td>
            <td>{{task.description}}</td>
            <td>
              <div class="text-center" @click="editTask(index)">
                <span class="fa fa-pen pointer"></span>
              </div>
            </td>
            <td>
              <div class="text-center" @click="deleteTask(index)">
                <span class="fa fa-trash pointer"></span>
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
      task: '',
      description: '',
      editedTask: null,

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
  },

  methods: {

    submitTask() {
      if (this.task.length === 0) return;

      if (this.editedTask === null){ 
        this.tasks.push({
        name: this.task,
        description: this.description,
      })

      this.task = '',
      this.description = ''

      } else {
        this.tasks[this.editedTask].name = this.task;
        this.tasks[this.editedTask].description = this.description
        this.editedTask = null;
        this.editedDescription = null;
      }
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask (index) {
      this.task = this.tasks[index].name;
      this.description = this.tasks[index].description;
      this.editedTask = index;
      this.editedDescription = index;
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
  .pointer {
    cursor: pointer;
  }
</style>
