<template>
    <div >
        {{ task }}
        <button class="remove" title="Удалить" @click="$emit('remove-task', task.id)">&times;</button>
    </div>
     <!-- @remove-task="removeTask" -->
</template>

<script>
export default {
    props: {
        task: {
            type: String,
            default: ''
        }
    },
    // methods: {
    //   removeTask(task) {
    //     this.$emit('remove-task', task)
    //   }
    // }
}
</script>

<style lang="scss" scoped>
  button {
    width: 20px;
    height: 20px;
    background-color: rgba(255, 255, 255, 0.4);
    border: none;
    color: gray;
    border-radius: 50%;
    position: absolute;
    top: 5px;
    right: 5px;
    text-align: center;
    line-height: 20px;
    outline: none;

    &:hover {
      cursor: pointer;
      transform: scale(1.07);
    }
  }
</style>