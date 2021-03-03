<template>
  <h2>Form Random Group</h2>
  <form @submit.prevent="calculateGroups">
    <div class="form-control">
      <label for="groups">Jumlah Kelompok</label>
      <input
        type="number"
        name="groups"
        id="groups"
        min="1"
        v-model.number="groupValue"
      />
    </div>
    <div class="form-control">
      <label for="persons">Jumlah Orang</label>
      <input
        type="number"
        name="persons"
        id="persons"
        min="1"
        v-model.number="personValue"
      />
    </div>
    <div class="form-control">
      <base-button type="submit" @click="randomGroups"
        >Acak Sekarang</base-button
      >
    </div>
  </form>
  <p v-if="error">
    Random Group Error. Masukkan Angka yang Nilainya Lebih dari 0.
  </p>
</template>

<script>
import chunk from 'lodash.chunk';
import shuffle from 'lodash.shuffle';

export default {
  data() {
    return {
      groupValue: null,
      personValue: null,
      error: false,
      resultArr: [],
      firstArr: [],
      secondArr: [],
    };
  },
  methods: {
    randomGroups() {
      this.resultArr = [];
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
        this.resultArr.push(i);
      }
      this.resultArr = shuffle(this.resultArr);

      const divideChunk = this.personValue / this.groupValue;
      const range = this.personValue - this.groupValue;

      if (divideChunk % 1 === 0) {
        this.resultArr = chunk(this.resultArr, divideChunk);
      } else if (this.groupValue > this.personValue) {
        this.resultArr = chunk(this.resultArr, Math.ceil(divideChunk));
      } else if (divideChunk % 1 !== 0 && range < this.groupValue) {
        this.primaryArr = this.resultArr.slice(0, this.groupValue);
        this.secondArr = this.resultArr.slice(
          this.groupValue,
          this.personValue
        );

        this.primaryArr = chunk(
          this.primaryArr,
          this.groupValue
        )[0].map((elem) => [elem]);

        for (let i = 0; i < this.secondArr.length; i++) {
          this.primaryArr[i].push(this.secondArr[i]);
        }

        this.resultArr = this.primaryArr;
      } else if (divideChunk % 1 !== 0 && range > this.groupValue) {
        const divide = Math.floor(this.personValue / this.groupValue);
        const totalEqual = divide * this.groupValue;

        this.primaryArr = this.resultArr.slice(0, totalEqual);
        this.secondArr = this.resultArr.slice(totalEqual, this.personValue);

        this.primaryArr = chunk(this.primaryArr, this.groupValue);

        for (let i = 0; i < this.secondArr.length; i++) {
          this.primaryArr[i].push(this.secondArr[i]);
        }

        this.resultArr = this.primaryArr;
      }
      // console.log(this.resultArr);
    },
  },
};
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
  border-color: #36c2e9;
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