<template>
  <div>
    <h2>{{name}}</h2>
    <hr/>
    <draggable v-model="tasks" group="people" @change="log">
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
  // data() {
  //   return {};
  // },
  methods: {
    addTask(task) {
      this.$emit('add-task', {column: this.name, task})
    },
    log(e) {
        if (e.removed) {
          this.removeTask(e.removed.element)
        }
        else if (e.added) {
          this.$emit('add-task', {column: this.name, task: e.added.element})
        }
    },
    removeTask(task) {
      this.$emit('remove-task', {column: this.name, task})
    }
  }
};
</script>

<style lang="scss" scoped>
h2 {
  width: 100%;
  color: rgb(44, 23, 61);
  text-transform: uppercase;
  text-align: center;
  font-weight: bold;
  font-size: 22px;
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  margin-bottom: 16px;
}
.task {
  width: 100%;
  min-height: 44px;
  margin: 20px 0;
  background-color: rgba(153, 121, 182, 0.5);
  border-radius: 8px;
  box-shadow: 0px 0px 19px -6px rgba(0,0,0,0.5);
  padding: 10px 30px 10px 10px;
  box-sizing: border-box;
  font-size: 16px;
  position: relative;
  font-family: 'Montserrat', sans-serif;
  overflow: hidden;
  text-overflow: ellipsis;
  word-wrap: break-word;
  line-height: 25.6px;
  

  &:hover {
    cursor: pointer;
    box-shadow: 0px 0px 19px -6px rgba(0,0,0,0.7);
  }
}
// .data-v-6e7fde86 {
//   padding: 15px;
// }
</style>