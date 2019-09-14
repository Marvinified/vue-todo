<template>
  <div>
    <nav>
      <h3>My Tasks</h3>
    </nav>
    <div class="home">
      <AddTodo :onAdd="add" />
      <div class="todos">
        <Todo
          v-for="todo in todos"
          :key="todo.id"
          :id="todo.id"
          :completed="todo.completed"
          :title="todo.title"
          :onToggle="toggle"
          :onDelete="remove"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo.vue";
import AddTodo from "@/components/AddTodo.vue";

export default {
  name: "home",
  components: {
    Todo,
    AddTodo
  },
  data: function() {
    return {
      todos: [
        {
          id: 1,
          title: "My First Task",
          completed: false
        },
        {
          id: 2,
          title: "My Second Task",
          completed: false
        }
      ]
    };
  },
  methods: {
    toggle: function(id) {
      this.todos = this.todos.map(todo => {
        if (todo.id === id) {
          return {
            ...todo,
            completed: !todo.completed
          };
        }
        return todo;
      });
    },
    remove: function(id) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== id;
      });
    },
    add: function(title) {
      console.log(title);
      this.todos.push({
        id: this.todos.length,
        title: title,
        completed: false
      });
    }
  }
};
</script>

<style scoped lang="scss">
nav {
  width: 100%;
  padding: 10px;
  box-shadow: 0 0 2px 2px #0001;
  margin: 10px;
}
.home {
  display: flex;
  width: 100%;
  /* flex-wrap: wrap; */
  /* height: 100vh; */
  /* align-items: center; */
  /* justify-content: center; */
}
.todos {
  display: flex;
  width: 100%;
  flex-wrap: wrap;
}
</style>
