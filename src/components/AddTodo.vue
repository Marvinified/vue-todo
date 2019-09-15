<template>
  <div class="todo-container">
    <div class="create-todo">
      <textarea type="text" v-model="title" placeholder="Add new Task" />
    </div>
    <div class="create-btn" @click="add">Create new task</div>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data: function() {
    return {
      title: ""
    };
  },
  props: {
    onAdd: Function
  },
  methods: {
    add: function() {
      if (this.title !== "") {
        this.onAdd(this.title);
        this.title = "";
      }
    },
    // onTextChange: function(e) {
    //   this.title = e.target.value;
    // }
  }
};
</script>

<style lang="scss" scoped>
.todo-container {
  padding: 10px;
}

.create-todo {
  width: 200px;
  padding: 10px;
  box-shadow: 0 0 2px 2px #0001;
  cursor: pointer;
  border-radius: 10px;
  textarea {
    border: 0;
    padding: 10px;
    outline: 0;
    width: 100%;
    box-sizing: border-box;
  }
}
.create-btn {
  padding: 10px;
  margin: 5px 0;
  background-color: rgb(44, 189, 140);
  color: rgb(255, 255, 255);
  box-shadow: 0 0 2px 2px #0001;
  cursor: pointer;
  border-radius: 10px;
}
</style>