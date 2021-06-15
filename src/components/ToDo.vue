<template>
  <div class="container">
    <div class="d-flex justify-content-around mb-5">
        <h3 class="mt-5">To do App</h3>
        <counter :number="this.tasks.length" class="mx-5"></counter>
    </div>
    <div class="d-flex justify-content-between">
      <input v-model="task" type="text" class="form-control mx-2" placeholder="Create your task">
      <button @click="addTask" class="btn btn-success rounded-1">Add</button>
    </div>
    <div>
      <h3>table view</h3>
  <table class="table table-hover mt-5">
        <thead>
          <tr>
            <th scope="col">Task</th>
            <th scope="col">Status</th>
            <th scope="col">Last</th>
            <th scope="col">Handle</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(task,index) in tasks" :key="index">
            <td :class="{'done': task.status === 'done'}">{{task.name}}</td>
            <td style="width: 120px"> <span class="pointer btn btn-outline-secondary" :class="{'btn btn-outline-success': task.status==='done','btn btn-outline-danger': task.status==='to-do','btn btn-outline-warning': task.status==='doing'}"  @click="changeStatus(index)">{{task.status}}</span></td>
            <td><span class="btn btn-secondary" @click="editTask(index)">Edit</span></td>
            <td><span class="btn btn-danger" @click="deleteTask(index)">Delete</span></td>
          </tr>
        </tbody>
</table>
    </div>
    <hr>
    <h3>card view</h3>
    <div class="row">
      <div class="col-sm-2"></div>
    <div class="col-sm-8">
     <div class="" v-for="(task,index) in tasks" :key="index" >
                <div class="card">
                  <div class="card-body">
                    <h5 :class="{'done': task.status === 'done'}" class="mx-5">{{task.name}}  <span class="pointer btn btn-outline-secondary mx-2" :class="{'btn btn-outline-success': task.status==='done','btn btn-outline-danger': task.status==='to-do','btn btn-outline-warning': task.status==='doing'}"  @click="changeStatus(index)">{{task.status}}</span>
                    <span class="btn btn-secondary mx-2" @click="editTask(index)">Edit</span>
                    <span class="btn btn-danger mx-2" @click="deleteTask(index)">Delete</span></h5>
                  </div>
              </div>
              <br>
            </div>
      </div>
      <div class="col-sm-2"></div>

    </div>
  </div>
  
</template>


<script>
import Counter from './Counter.vue'
export default {
  name: 'ToDo',
  components:{'counter':Counter},
  methods:{
    addTask(){
      if(this.task.length === 0) return
      if (this.editTaskIndex === null ){
          this.tasks.push({name:this.task,status:"to-do"})
          this.task = ""
      }else{
        this.tasks[this.editTaskIndex].name = this.task;
        this.editTaskIndex = null;
        this.task = ""
      }
      
    },
    deleteTask(index){
      this.tasks.splice(index,1);
    },
    editTask(index){
      this.task = this.tasks[index].name;
      this.editTaskIndex = index;
    },
    changeStatus(index){
      let newIndex = this.statusList.indexOf(this.tasks[index].status)
      if(++newIndex > 2 )newIndex=0
      this.tasks[index].status= this.statusList[newIndex]
    }
  },
  data(){
    return{
      task:"",
      editTaskIndex:null,
      statusList:["to-do","doing","done"],
      tasks:[
        {name:"Print the pdf soon", status:"to-do"},
        { name:"Learn vue js",status:"done"}
      ],
      
    }
  }
}
</script>

<style scoped>
.done{
  text-decoration: line-through;
}
</style>
