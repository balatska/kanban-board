<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title"/>
    <button type="submit" title="Добавить">+</button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTask = {
          title: this.title,
        };

        this.$emit("add-task", newTask);
        this.title = "";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
form {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
button {
  border: none;
  background-color: rgba(153, 121, 182, 1);
  width: 30px;
  height: 30px;
  border-radius: 50%;
  font-size: 20px;
  font-weight: bold;
  outline: none;

  &:hover {
    cursor: pointer;
    transform: scale(1.07);
  }
}
input {
  width: 80%;
  height: 20px;
  padding: 0 5px;
  box-sizing: border-box;
  // width: 100%;
  border-radius: 4px;
  border: 1px solid grey;
  outline: none;
}
</style>