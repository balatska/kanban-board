<template>
    <div >
        {{ task.title }}
        <button class="remove" title="Удалить" @click="$emit('remove-task', task)">&times;</button>
    </div>
</template>

<script>
export default {
    props: {
        task: {
            type: Object,
        }
    },
}
</script>

<style lang="scss" scoped>
  button {
    width: 22px;
    height: 22px;
    background-color: rgba(255, 255, 255, 0.4);
    border: none;
    color: gray;
    border-radius: 50%;
    position: absolute;
    top: calc(50% - 11px);
    right: 10px;
    text-align: center;
    line-height: 20px;
    outline: none;

    &:hover {
      cursor: pointer;
      transform: scale(1.07);
    }
  }
</style>