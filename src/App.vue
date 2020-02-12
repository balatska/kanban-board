<template>
  <div id="app">
    <h1>Personal Kanban board</h1>
    <div class="container">
      <Column class="column"
        v-for="(column, i) in board"
        :key="i"
        :tasks="column.tasks"
        :name="column.name"
        @add-task="newTask"
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
    removeTask({column, task}) {
      const col = this.board.findIndex(item => item.name === column)
      const item = this.board[col].tasks.findIndex(item => item.id === task.id)
      this.board[col].tasks.splice(item, 1)      
    },
    newTask({column, task}) {
      this.board[this.board.findIndex(item => item.name === column)].tasks.push(task)
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
            { id: 5, title: "Купить платье" },
          ] 
        },
        { 
          name: "in progress", 
          description: "in progress...", 
          id: 3,
          tasks: [
            { id: 6, title: "Защитить проект" }
          ] 
        },
        { 
          name: "done", 
          description: "done...", 
          id: 4,
          tasks: [
            { id: 7, title: "Записаться на курс в Beetroot" },
            { id: 8, title: "Сделать настоящее тестовое" }
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
  box-shadow: 0px 0px 22px -6px rgba(0,0,0,0.2);
  padding: 25px;
  border-radius: 8px;

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
  color: rgb(48, 20, 61);
  margin: 30px 0;
  font-family: 'Montserrat', sans-serif;
  font-weight: bold;
}
</style>


