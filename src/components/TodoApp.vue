<template>
    <div class="container">

        <h2 class="text-center mt-5">My Vue Todo App</h2>
        <!-- input -->
        <div class="d-flex">
            <input v-model="task" type="text" placeholder="Enter task" class="form-control">
            <button @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>
        </div>

        <!-- Task table -->
        <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">$$$</th>
      <th scope="col" class="text-center">###</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" :key="index">
      <td>{{task.name}}</td>
      <td>{{task.status}}</td>
      
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
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
    name: "HelloWorld",
    props: {
        msg: String,
    },
    
    data(){
      return {
        task: '',
        editedTask: null,
        tasks: [
          {
            name: ' Mastering with wadud akond ' ,
            status: 'javascript'
          },
          {
            name: 'Begainner saikat hasan',
            status: 'novice'
          }
        ]
      }
    },

    methods: {
     submitTask(){
       if(this.task.length === 0) return;

      if(this.editedTask === null){
        this.tasks.push({
        name: this.task,
        status: 'to-do'
        });

      }else{

        this.tasks[this.editedTask].name = this.task;

      }
      
        this.task = '';
     },
      deleteTask(index){
        this.tasks.splice(index, 1);
      },

      editTask(index){
        this.task = this.tasks[index].name;
        this.editedTask = index;
      }
    }
  };



</script>