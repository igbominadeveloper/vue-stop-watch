<template>
  <button @click="$emit('click')">
    <slot>Start</slot>
  </button>
</template>

<script>
export default {
  name: 'AppButton',
};
</script>

<style scoped>
button {
  background-color: var(--color-primary);
  color: var(--color-secondary);
  font-size: 1em;
  font-weight: 600;

  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  width: 80%;
}

button:hover {
  background-color: var(--color-secondary);
  color: var(--color-primary);
  transition: background-color 0.3s ease-in-out;
}
</style>
