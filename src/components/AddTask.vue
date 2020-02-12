<template>
  <form @submit.prevent="onSubmit">
    <input type="text" placeholder="Добавить задачу" v-model="title"/>
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
          id: Date.now(),
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
  position: relative;
}
button {
  border: none;
  background-color: rgba(153, 121, 182, 1);
  width: 30px;
  height: 30px;
  border-radius: 50%;
  font-size: 26px;
  font-weight: bold;
  outline: none;
  color: #ffffff;
  position: absolute;
  right: 10px;
  top: 7px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0;

  &:hover {
    cursor: pointer;
    transform: scale(1.07);
  }
}
input {
  width: 100%;
  height: 44px;
  padding: 0 45px 0 10px;
  box-sizing: border-box;
  border-radius: 8px;
  border: 1px solid rgb(201, 201, 201);
  outline: none;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  color: rgb(201, 201, 201);
}
</style>