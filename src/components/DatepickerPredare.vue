<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <Datepicker v-model="date" :format="format" :min-date="new Date()" :max-date="maxDate" prevent-min-max-navigation
      :enable-time-picker="false" autocomplete="off" placeholder="Selecteaza data de predare"
      :day-names="['Lu', 'Ma', 'Mi', 'Jo', 'Vi', 'Sa', 'Du']"
      cancel-text="Inchide"
      select-text="Selecteaza"
      :format-locale="ro"
      auto-apply />

    <Datepicker v-model="time" :start-time="startTime" time-picker minutes-increment="15" minutes-grid-increment="15"
      autocomplete="off" placeholder="Selecteaza ora de predare" style="margin-top: 10px;" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { ro } from 'date-fns/locale';
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

// import { inject } from 'vue';
// const selectedDate = inject('selectedDate');

const date = ref(addDays(new Date(), 4));
const startTime = ref({ hours: new Date().getHours(), minutes: 0 });

const time = ref({
  hours: new Date().getHours(),
  minutes: "00"
});

const format = (date) => {
  const day = date.getDate();
  const month = date.getMonth() + 1;
  const year = date.getFullYear();

  return `${day}/${month}/${year}`;
}

function addDays(date, days) {
  var result = new Date(date);
  result.setDate(result.getDate() + days);
  return result;
}

</script>
