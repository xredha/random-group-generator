<template>
  <div>
    <h1>{{title}}</h1>
  </div>
</template>

<script>
export default {
  props: ['title'],
}
</script>

<style scoped>
div {
  background-color: #36C2E9;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 5rem;
}
h1 {
  font-weight: 200;
  margin: 0;
  padding: 1rem;
  color: white;
}
</style>