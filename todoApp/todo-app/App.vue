<template>
  <view class="container">
    <Header title="TodoApp" />

    <view class="inputContainer">
      <text-input class="text-input" v-model="newTodoText" />
      <touchable-opacity class="add-btn" :on-press="newTodo">
        <text class="btn-text">Adicionar</text>
      </touchable-opacity>
    </view>

    <view class="todo" v-for="todo in todos" :key="todo.id">
      <touchable-opacity :on-press="() => toggleDone(todo.id)">
        <text class="todo-text done" v-if="todo.done">{{ todo.title }}</text>
        <text class="todo-text" v-else>{{ todo.title }}</text>
      </touchable-opacity>
      <touchable-opacity class="remove-btn" :on-press="() => removeTodo(todo.id)">
        <text class="remove-todo">Remover</text>
      </touchable-opacity>
    </view>
  </view>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  data() {
    return {
      newTodoText: "",
      todos: [
        {
          id: 0,
          title: "Teste TODO",
          done: false
        }
      ]
    };
  },
  components: {
    Header
  },
  methods: {
    newTodo() {
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodoText,
        done: false
      });
    },
    toggleDone(id) {
      this.todos = this.todos.map(td => {
        if (td.id === id) td.done = !td.done;
        return td;
      });
    },
    removeTodo(id) {
      this.todos = this.todos.filter(td => td.id !== id);
    }
  }
};
</script>

<style>
.container {
  background-color: white;
  flex: 1;
}
.inputContainer {
  flex-direction: row;
  justify-content: center;
  align-items: stretch;
}
.text-input {
  flex: 1;
  height: 35px;
  background-color: #f3f3f3;
  font-size: 19px;
  color: #000;
}
.add-btn {
  width: 100px;
  height: 35px;
  background-color: #ffcc00;
  justify-content: center;
  align-items: center;
}
.btn-text {
  font-size: 18px;
  font-weight: 700;
}
.todo {
  flex-direction: row;
  justify-content: space-between;
  padding: 20px;
}
.todo-text {
  font-size: 20px;
}
.done {
  color: #aaaaaa;
}
.remove-todo {
  color: red;
  font-size: 18px;
}
</style>
