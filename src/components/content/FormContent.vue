<template>
  <h2>Form Random Group</h2>
  <form @submit.prevent="calculateGroups">
    <div class="form-control">
      <label for="groups">Jumlah Kelompok</label>
      <input type="number" name="groups" id="groups" min="1" v-model.number="groupValue">
    </div>
    <div class="form-control">
      <label for="persons">Jumlah Orang</label>
      <input type="number" name="persons" id="persons" min="1" v-model.number="personValue">
    </div>
    <div class="form-control">
      <base-button type="submit" @click="randomGroups">Acak Sekarang</base-button>
    </div>
  </form>
  <p v-if="error">Random Group Error. Masukkan Angka yang Nilainya Lebih dari 0.</p>
</template>

<script>
import chunk from 'lodash.chunk';
import shuffle from 'lodash.shuffle';

export default {
  data() {
    return {
      groupValue: 1,
      personValue: 1,
      error: false,
      result: [],
    }
  },
  methods: {
    randomGroups() {
      this.result = [];
      if (this.groupValue < 0 || this.personValue < 0) {
        this.error = true;
        return;
      } else if (this.groupValue % 1 !== 0 || this.personValue % 1 !== 0) {
        this.error = true;
        return;
      } else if (this.groupValue === 0 || this.personValue === 0) {
        this.error = true;
        return;
      }

      for (let i = this.personValue; i >= 1; i--) {
        this.result.push(i);
      }
      let divider = Math.round(this.personValue/this.groupValue);
      console.log(divider);
      this.result = shuffle(this.result);
      this.result = chunk(this.result, divider);
      console.log(this.result);
    }
  }
}
</script>

<style scoped>
h2 {
  text-align: center;
  margin: 0;
}

label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #36C2E9;
  background-color: rgb(201, 230, 245);
}

.form-control {
  margin: 1rem 0;
}

p {
  font-weight: 400;
  color: red;
}
</style>