<script setup lang="ts">
import { reactive } from '@vue/reactivity';
import TodoList from '../components/TodoList.vue';

const todos = reactive([
  { title: "Buy food", done: true, id: "1" },
  { title: "Do laundry", done: true, id: "2" },
  { title: "Sleep", done: true, id: "3" },
  { title: "Eat", done: true, id: "4" },
  { title: "Pray", done: true, id: "5" },
  { title: "Watch Dr Strange 2", done: false, id: "6" },
]);

const addTodo = (e: InputEvent) => {
  const title = (e.target as HTMLInputElement).value;

  todos.unshift({
    title,
    done: false,
    id: todos.length.toString(),
  });

  (e.target as HTMLInputElement).value = '';
};

const removeTodo = (index: number) => {
  todos.splice(index, 1);
};
</script>

<template>
  <main>
    <h1>Todo Example</h1>
    <input placeholder="Add a todo" @keyup.enter="addTodo">
    <todo-list :todos="todos" @remove-todo="removeTodo"/>
  </main>
</template>
<style scoped>
main {
  display: grid;
  grid-gap: 1rem;
}

input {
  padding: 0.5rem;
}
</style>
