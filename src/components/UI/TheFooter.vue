<template>
  <div>
    <p>{{title}} &copy; 2021. Created by <a :href="link" target="_blank">{{contributor}}</a>. Made with ❤️.</p>
  </div>
</template>

<script>
export default {
  props: ['title', 'link', 'contributor'],
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
p {
  font-weight: 300;
  margin: 0;
  padding: 1rem;
  color: white;
}
a {
  text-decoration: none;
  color: inherit;
}
a:hover {
  color: #ccc;
}
</style>