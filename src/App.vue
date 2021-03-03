<template>
  <the-header :title="title"></the-header>
  <main-content></main-content>
  <the-footer
    :title="title"
    :link="link"
    :contributor="contributor"
  ></the-footer>
</template>

<script>
import TheHeader from './components/UI/TheHeader.vue';
import MainContent from './components/content/MainContent.vue';
import TheFooter from './components/UI/TheFooter.vue';

export default {
  components: {
    TheHeader,
    MainContent,
    TheFooter,
  },
  data() {
    return {
      title: 'Random Group Generator',
      link: 'https://github.com/xredha',
      contributor: 'Galih Redha Saputra',
    };
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400&display=swap');
body {
  margin: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
</style>
