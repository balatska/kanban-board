<template>
  <div id="app">
    <h1>Kanban board</h1>
    <hr />
    <div class="container">
      <Column class="column"
        v-for="(column, i) in board"
        :key="i"
        :tasks="column.tasks"
        :name="column.name"
        @remove-task="removeTask"
      />
    </div>
  </div>
</template>
 
<script>
import Column from "@/components/Column";

export default {
  name: "app",
  components: {
    Column
  },
  methods: {
    removeTask(task) {
      // this.tasks = this.tasks.filter(t => t.task !==task)
      console.log(this.tasks) 
    }
  },
  data() {
    return {
      board: [
        { 
          name: "ideas", 
          description: "ideas", 
          tasks: [
            { id: 1, title: "Выучить Vue" },
            { id: 2, title: "Отпраздновать выпуск" },
            { id: 3, title: "Найти работу" },
            { id: 4, title: "Не унывать" }
          ] 
        },
        { 
          name: "todo", 
          description: "to do...", 
          tasks: [
            { id: 1, title: "Выучить Vue" },
          ] 
        },
        { 
          name: "in progress", 
          description: "in progress...", 
          tasks: [
            { id: 4, title: "Не унывать" }
          ] 
        },
        { 
          name: "done", 
          description: "done...", 
          tasks: [
            { id: 3, title: "Найти работу" },
            { id: 4, title: "Не унывать" }
          ] 
        }]      
    };
  }
};
</script>
 
<style lang="scss" scoped>
body {
  margin: 0 auto;
  width: 100%;
  height: 100vh;
  // background-image: url(@/assets/img3.jpg);
}
// #app {

// }
.column {
  // width: 240px;
  width: 18%;
  height: auto;
  margin-top: 10px;
  box-shadow: 0px 0px 19px -4px rgba(0,0,0,0.5);
  padding: 25px;
  border-radius: 4px;
}
.container {
  display:flex;
  justify-content:space-evenly;
}
h1 {
  text-align: center;
}
</style>


