<template>
  <div>
    {{ statuses }}
    <!-- <Task 
    :tasks="tasks" 
    v-for="(task, index) in tasks" :key="index"
    /> -->
  </div>
</template>

<script>
import Task from "@/components/Task";
export default {
  props: ["statuses"],
  components: {
    Task
  },
  data() {
    return {
      tasks: [
        { id: 1, title: "Выучить Vue" },
        { id: 2, title: "Отпраздновать выпуск из Beetroot" },
        { id: 3, title: "Найти работу" },
        { id: 4, title: "Не унывать" }
      ]
    } 
  }
};
</script>