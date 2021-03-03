<template>
  <main>
    <base-card>
      <form-content></form-content>
    </base-card>
  </main>
</template>

<script>
import FormContent from './FormContent.vue';

export default {
  components: {
    FormContent,
  },
};
</script>

<style scoped>
main {
  min-height: 80vh;
}
</style>