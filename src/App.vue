<template>
  <div class="contanier mt-5">
    <div class="row">
      <div class="col form-inline">
        <input v-model ="newTask" placeholder="Enter Task" @keyup.enter="add"> 
        <button class="primary" @click="add">Add</button>
      </div>
    </div>
    
    <div class="row">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>Backlog</h3>
          <draggable class="list-group kanban-columns" :list="arrBacklog" group="tasks">
            <div class="list-group-item" v-for ="element in arrBacklog" :key="element.name"  >
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group kanban-columns" :list="arrInprogress" group="tasks">
            <div class="list-group-item" v-for ="element in arrInprogress" :key="element.name"  >
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Test</h3>
          <draggable class="list-group kanban-columns" :list="arrTested" group="tasks">
            <div class="list-group-item" v-for ="element in arrTested" :key="element.name"  >
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>

       <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group kanban-columns" :list="arrDone" group="tasks">
            <div class="list-group-item" v-for ="element in arrDone" :key="element.name"  >
              {{element.name}}
            </div>
          </draggable>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name : 'App',
  components : {
    draggable  
  },
  data(){
    return {
      newTask : "",
      arrBacklog : [
        {name : "Code SignupPage"},
        {name : "Test Dashboard"},
        {name : "Style Design"},
        {name : "Help with design"},
      ],
      arrInprogress : [],
      arrTested : [],
      arrDone : []
    }
  },
  methods : {
    add(){
      if(this.newTask){
        this.arrBacklog.push({name : this.newTask})
        this.newTask = ""
      }
    }
  }

}
</script>

<style>

.kanban-columns {
  min-height: 300px;
}

</style>
