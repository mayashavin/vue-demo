<template>
  <transition-group name="list" tag="ul">
    <!-- <ul> -->
    <li v-for="(todo, index) in todos" :key="todo.id" class="list-item">
      <label :for="getTodoInputId(todo.id)" @click="todo.done = !todo.done">
        <input
          type="checkbox"
          :id="getTodoInputId(todo.id)"
          v-model="todo.done"
        />
        {{ todo.title }}
      </label>
      <button @click="removeTodo(index)">X</button>
    </li>
    <!-- </ul> -->
  </transition-group>
</template>
<script lang="ts" setup>
const props = defineProps({
  todos: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["removeTodo"]);

const getTodoInputId = (id: string) => `todo-${id}`;

const removeTodo = (index: number) => {
  emit("removeTodo", index);
};
</script>
<style scoped>
ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  margin: 0.2rem 0;
  background: #eee;
  border-radius: 0.5rem;
  gap: 0.5rem;
}

label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8rem;
}

button {
  cursor: pointer;
  border: none;
}

button:hover,
button:focus,
button:active {
  color: #b13c3c;
}

.list-enter-active,
.list-leave-active {
  transition: all 1s;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
