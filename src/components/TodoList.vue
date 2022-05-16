<template>
  <div>Todo</div>
</template>
<script lang="ts" setup>
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
