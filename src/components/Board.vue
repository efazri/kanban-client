<template>
  <div>
    <TaskLists v-for="(category, i) in categories"
    :key="i"
    :category="category"
    :assignments="tasks"
    class="shadow-lg p-3 mb-5 bg-white rounded" 
    id="boardTask"
    @emitEdit="edit"
    @addTask="addTask"
    ></TaskLists>
  </div>
</template>

<script>
import TaskLists from './TaskLists'

export default {
    name:'Board',
    data (){
        return {
            categories: ['backlog', 'to-do', 'doing', 'done']
        }
    },
    methods: {
      edit(data){
        this.$emit('editTask', data)
      },
      
      addTask(){
        this.$emit('addTask', 'create')
      }

    },
    props: ['tasks'],
    components :{
      TaskLists
    }
}
</script>

<style scope>
#boardTask{
  width: 250px;
  border: solid #E6E6E6 1px;
}
</style>