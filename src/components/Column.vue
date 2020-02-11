<template>
  <div>
    <h2>{{name}}</h2>
    <hr/>
    <draggable v-model="tasks" group="people" @start="drag=true" @end="drag=false">
      <Task class="task" 
      v-for="task in tasks" 
      :key="task.id" 
      :task="task"
      @remove-task="removeTask"
      >
      </Task> 
    </draggable>
    <AddTask @add-task="addTask"/> 
  </div>
</template>

<script>
import Task from "@/components/Task";
import AddTask from "@/components/AddTask";
import draggable from 'vuedraggable'
export default {
  props: {
    name: {
      type: String,
      default: ''
    }, 
    tasks: {
      type: Array, 
      default: []
    }
  },
  components: {
    Task, AddTask, draggable,
  },
  data() {
    return {};
  },
  methods: {
    addTask(task) {
      this.tasks.push(task)
    },
    removeTask(id) {
      // this.$emit('remove-task', id) {
      //   this.$emit(id)
      // }

      // this.$emit('remove-task', {
      //   taskId: id,
      //   columnId: this.columnId
      // });
    }
  }
};
</script>

<style lang="scss" scoped>
h2 {
  width: 100%;
  color: #112e7e;
  text-transform: uppercase;
  text-align: center;
  font-weight: bold;
  font-size: 28px;
}
.task {
  width: 100%;
  height: 60px;
  margin: 20px 0;
  background-color: rgba(153, 121, 182, 0.5);
  border-radius: 4px;
  box-shadow: 0px 0px 19px -6px rgba(0,0,0,0.5);
  padding: 10px;
  box-sizing: border-box;
  font-size: 16px;
  position: relative;
  

  &:hover {
    cursor: pointer;
    box-shadow: 0px 0px 19px -6px rgba(0,0,0,0.7);
  }
}
.data-v-6e7fde86 {
  padding: 15px;
}
</style>