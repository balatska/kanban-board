<template>
  <div id="app">
    <h1>Kanban board</h1>
    <hr>
    <Column 
    :statuses="statuses"
    />
        <!-- v-for="(status, index) in statuses" :key="index"
    :status="status" -->
  </div>
</template>
 
<script>
import Column from '@/components/Column'
export default {
  name: 'app',
  components: {
    Column,
  },
  data () {
    return {
      statuses: ['Ideas', 'To do', 'In progress', 'Done'],
      tasks: [],
    }
  }
}
</script>
 
<style lang="scss" scoped>
  #app {
    background-color: #b9e7e7;
  }
 
  h1 {
    text-align: center;
  }
</style>


