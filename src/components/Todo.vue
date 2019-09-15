<template>
  <div class="todo-container">
    <span class="todo" @click="toggle">
      <input
        type="checkbox"
        v-model="completed"
        v-bind:value="title"
        v-bind:name="title"
      />
      <span class="title">{{title}}</span>
    </span>
    <v-icon class="delete-todo" @click="remove" v-text="'$vuetify.icons.cancel'"></v-icon>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    id: Number,
    title: String,
    completed: Boolean,
    onToggle: Function,
    onDelete: Function,
    description: String
  },
  methods: {
    toggle: function() {
      this.onToggle(this.id);
    },
    remove: function() {
      this.onDelete(this.id);
    }
  }
};
</script>

<style lang="scss" scoped >
.todo-container {
  height: fit-content;
  display: flex;
  padding: 10px;
  &:hover {
    & > .delete-todo {
      visibility: visible;
    }
  }
}
.title {
  word-break: break-word;
  padding: 5px;
  text-align: left;
}
.todo {
  width: 200px;
  padding: 10px;
  box-shadow: 0 0 2px 2px #0001;
  border-radius: 0px 10px 0px 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  input {
    width: 24px;
    height: 24px;
  }
}

.delete-todo {
  visibility: hidden;
}
</style>