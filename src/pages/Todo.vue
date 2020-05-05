<template>
  <q-page class="bg-grey-3 column"> 
    <div class="row q-pa-sm bg-primary"><q-input  @keyup.enter="addTask" bg-color="white"  class="col" square v-model="newTask" placeholder="Add Task"  filled dense>
        <template v-slot:before>
          <q-icon name="event" />
        </template>

        <template v-slot:hint>
          Field hint
        </template>

        <template v-slot:append>
          <q-btn 
          round
          dense 
          flat
         icon="add"
         @click="addTask" />
        </template>
      </q-input></div>
     <q-list class="bg-white"
     separator bordered>
      <!--
        Rendering a <label> tag (notice tag="label")
        so QCheckboxes will  respond to clicks on QItems to
        change Toggle state.
      -->

      <q-item  v-for="(task,index) in tasks"
      :key="task.title"  
      @click="task.done=!task.done" clickable
      :class="{'done bg-blue-1':task.done}"
      v-ripple>
        <q-item-section avatar>
        <q-checkbox  v-model="task.done" val="teal" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
        <q-btn flat round dense color="primary" icon="delete"  @click.stop="deleteTask()"/>
        </q-item-section>
       
      </q-item>
    </q-list>
    <div class="no-tasks absolute-center"
     v-if="!tasks.length">
         <q-icon
         name="check"
         color="primary"
         size="100px"/>
        <div class="text-h5 text-primary text-center">No Tasks</div>
    </div>
     
  </q-page>
</template>
<script>
export default {
  name: 'PageIndex',
  props:['message'],
  data(){
    return {
      newTask:'',
      message:"good girl",

      tasks:[
        /*{
          title:"Get Bananas",
          done:false


        },
        {  
          title:"Get Apples",
          done:false

        },
        {
          title:"Get pomegranates",
          done:false
        }*/
      ]



    }


  }
  ,
methods:{

deleteTask(index){
        this.$q.dialog({
        title: 'Confirm',
        message: 'Would you like to delete the task?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index,1)
         this.$q.notify({
         message: 'Task has been deleted',
         color: 'purple'
      })
      })
},
addTask()
{
    this.tasks.push({
    title:this.newTask,
    done:false

  })
  this.newTask=""
}


  }
}
</script>
<style lang="scss">
.done{
  .q-item__label{
    text-decoration: line-through;
    color: #bbbb;
  }
  
}

</style>