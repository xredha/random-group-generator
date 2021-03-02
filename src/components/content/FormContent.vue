<template>
  <form @submit.prevent="calculateGroups">
    <div class="form-control">
      <label for="groups">Jumlah Kelompok</label>
      <input type="number" name="groups" id="groups">
    </div>
  </form>
</template>

<style scoped>
.form-control {
  margin: 1rem 0;
}
</style>