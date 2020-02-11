<template>
  <div id="app">
    <h1>Personal Kanban board</h1>
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
    removeTask(id) {
      // this.tasks = this.tasks.filter(t => t.id !==id)
      // console.log() 
    }
  },
  data() {
    return {
      board: [
        { 
          name: "ideas", 
          description: "ideas", 
          id: 1,
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
          id: 2,
          tasks: [
            { id: 1, title: "Купить платье" },
          ] 
        },
        { 
          name: "in progress", 
          description: "in progress...", 
          id: 3,
          tasks: [
            { id: 4, title: "Защитить проект" }
          ] 
        },
        { 
          name: "done", 
          description: "done...", 
          id: 4,
          tasks: [
            { id: 3, title: "Записаться на курс в Beetroot" },
            { id: 4, title: "Сделать настоящее тестовое" }
          ] 
        }]      
    };
  }
};
</script>
 
<style lang="scss" scoped>
.column {
  width: 18%;
  height: auto;
  min-height: 400px;
  margin-top: 10px;
  box-shadow: 0px 0px 19px -4px rgba(0,0,0,0.5);
  padding: 25px;
  border-radius: 4px;

  &>div {
    padding: 15px;
  }
}
.container {
  display:flex;
  justify-content:space-evenly;
}
h1 {
  text-align: center;
  text-transform: uppercase;
  color: rgb(68, 67, 67);
  margin: 30px 0;
}
</style>


