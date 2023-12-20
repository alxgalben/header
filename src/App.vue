<script setup>
import DatepickerPreluare from './components/DatepickerPreluare.vue';
import DatepickerPredare from './components/DatepickerPredare.vue';

</script>

<template>
  <div class="all" style="height: 100vh; z-index: 1000; position: relative; width: 25%; margin-left: 100px; text-align: center;">
  <div v-if="!showSecondSearchBox" class="card search-box">
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <select class="form-select form-select-sm" aria-label=".form-select-sm example" style="height: 40px;">
          <option selected>Locatie de preluare</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>

        <div class="predare-alta-locatie-check" style="margin-top: 5px;">
          <input @click="showField = !showField" class="form-check-input" type="checkbox" value="" id="flexCheckDefault">
          <label class="form-check-label" for="flexCheckDefault" style="font-size: 13px; margin-left: 7px;">
            Doresc sa predau masina in alta locatie
          </label>
        </div>

        <select v-if="showField" class="form-select form-select-sm" aria-label=".form-select-sm example"
          style="height: 40px; margin-top: 5px;">
          <option selected>Locatie de predare</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>

      </li>
      <li class="list-group-item">
        <DatepickerPreluare />
      </li>
      <li class="list-group-item">
        <DatepickerPredare />
      </li>
    </ul>
    <button type="button" class="btn btn-warning btn-search">Search</button>
    <button @click="toggleSearchBoxes" type="button" class="btn btn-dark btn-transfer-privat">{{ buttonText }}</button>
  </div>

  <div v-if="showSecondSearchBox" class="card search-box">
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <select class="form-select form-select-sm" aria-label=".form-select-sm example" style="height: 40px;">
          <option selected>Locatie de preluare</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>
      </li>
      <li class="list-group-item">
        <select class="form-select form-select-sm" aria-label=".form-select-sm example"
          style="height: 40px; margin-top: 5px;">
          <option selected>Locatie de predare</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>
      </li>
    </ul>
    <button type="button" class="btn btn-warning btn-search">Search</button>
    <button @click="toggleSearchBoxes" type="button" class="btn btn-dark btn-transfer-privat">{{ buttonText }}</button>
  </div>
</div>
</template>

<style>

.all {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.search-box {
  width: 25%;
  margin-left: 5%;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.btn-search {
    width: 95%;
    border-radius: 0;
    margin: 10px auto;
  }
  
  .btn-transfer-privat {
    width: 95%;
    border-radius: 0;
    margin: 10px auto;
    margin-top: 0px;
  }

  @media only screen and (max-width: 1310px) {
    .search-box {
  width: 35%;
  margin-left: 5%;
  }
}

@media only screen and (max-width: 700px) {
  .search-box {
  width: 45%;
}
}

@media only screen and (max-width: 600px) {

  .all {
    align-items: start;
  }

  .search-box {
    width: 90%;
    margin: 100px auto 0;
    border-radius: 0;
    text-align: center;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .form-select-sm:hover {
    cursor: pointer;
  }

  .btn-search {
    width: 95%;
    border-radius: 0;
    margin: 10px auto;
  }

  .privat {
    width: 90%;
    margin: 15px auto 0;
    text-align: right;
  }
}
</style>

<script>
export default {
  name: "app",
  data() {
    return {
      showField: false,
      showSecondSearchBox: false,
      buttonText: "Vreau transfer privat",
    };
  },
  methods: {
    toggleSearchBoxes() {
      this.showField = false;
      this.showSecondSearchBox = !this.showSecondSearchBox;
      this.buttonText = this.showSecondSearchBox ? "Vreau inchiriere auto" : "Vreau transfer privat";
    },
  },
};
</script>

