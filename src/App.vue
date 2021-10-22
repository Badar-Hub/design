<template>
  <Header class="q-py-md text-white" @date-changed="onDateChanged" />
  <div v-if="!isLoading" class="row bg-white">
    <div
      :class="selectedField === 'All' ? 'brdr-b' : ''"
      class="col-xs-4 text-center"
    >
      <q-btn
        @click="selectedField = 'All'"
        class="full-width q-my-sm"
        flat
        size="16px"
        label="All"
      />
    </div>
    <div
      :class="selectedField === 'Live' ? 'brdr-b' : ''"
      class="col-xs-4 text-center"
    >
      <q-btn
        @click="selectedField = 'Live'"
        class="full-width q-my-sm"
        flat
        size="16px"
        label="Live"
      />
    </div>
    <div
      :class="selectedField === 'Favorites' ? 'brdr-b' : ''"
      class="col-xs-4 text-center"
    >
      <q-btn
        @click="selectedField = 'Favorites'"
        class="full-width q-my-sm"
        flat
        size="16px"
        label="Favorites"
      />
    </div>
  </div>
  <div v-if="!isLoading" class="grid-row full-width">
    <Card :data="data.league" />
  </div>
</template>

<script>
import {  ref, watch } from 'vue';
import Card from './components/Card.vue';
import Header from './components/Header.vue';
const link = require('./assets/mockData/data.json');

export default {
  name: 'App',
  components: {
    Header,
    Card,
  },
  setup() {
    const data = ref([]);
    const selectedField = ref('All');
    const selectedDate = ref("Today");
    const isLoading = ref(true);

    const getMatchesData = async () => {
      isLoading.value = true;
      const res = link.data.find((x) => x.date === selectedDate.value);
      data.value = { ...res };
      try {
        if (selectedField.value === 'Live') {
          data.value.league = data.value.league.filter((x) => x.isLive);
        } else if (selectedField.value === 'Favorites') {
          data.value.league = data.value.league.filter((x) => x.isFavorite);
        }
      } catch (error) {
        console.log(error);
      } finally {
        isLoading.value = false;
      }
    };

    const onDateChanged = (newDate) => {
      switch (newDate) {
        case "Yesterday":
          selectedDate.value = "21-10-2021";
          break;
        case "Today":
          selectedDate.value = "22-10-2021";
          break;
        case "Tomorrow":
          selectedDate.value = "23-10-2021";
          break;
      }
    }

    watch(
      () => selectedField.value,
      () => getMatchesData()
    );

    watch(
      () => selectedDate.value,
      () => getMatchesData()
    );

    return {
      link,
      data,
      isLoading,
      selectedDate,
      selectedField,
      onDateChanged
    };
  },
};
</script>

<style>
body {
  background-color: #f1f1f1;
}
.brdr-b {
  border-bottom: 3px solid green;
}
.grid-row {
  display: grid;
  padding: 3px;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
</style>
