<template>
  <h1>{{ title }}</h1>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
  },
};
</script>


<style scoped>
h1 {
  font-size: 2em;

  margin: 20px 0;
}
</style>